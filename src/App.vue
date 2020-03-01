<template>
  <form
  @submit="checkForm"
>
  <p>
    <label for="username">email: </label>
    <input
      id="username"
      v-model="username"
      type="text"
      name="username"
    >
  </p>

  <p>
    <label for="password">password: </label>
    <input
      id="password"
      v-model="password"
      type="text"
      name="password"
    >
  </p>

  <p>
    <input
      type="submit"
      value="Submit"
    >
  </p>

</form>
</template>

<script>
export default {
  data () {
    return {
      postBody: '',
      errors: []
    }
  },
  formSubmit () {
    const postObj = this
    this.axios.post('http://localhost:3000/api/v1/login',
      {
        username: this.username,
        password: this.password
      })
      .then(function (response) {
        postObj.output = response.data
        console.log(postObj.output.code)
      })
      .catch(function (error) {
        postObj.output = error
      })
  }
}
</script>
