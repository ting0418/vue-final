<template><div>dash</div></template>

<script>
export default {
  created () {
    const token = document.cookie.replace(
      /(?:(?:^|.*;\s*)hexToken\s*=\s*([^;]*).*$)|^.*$/,
      '$1'
    )

    console.log(token)

    this.$http.defaults.headers.common.Authorization = token

    const api = `${process.env.VUE_APP_API}api/user/check`
    console.log(api)

    this.$http
      .post(api, this.user)
      .then((res) => {
        console.log(res)
      })
      .catch((error) => {
        console.error(error)
      })
  }
}
</script>
