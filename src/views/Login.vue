<template>
  <div class="cart mt-5 pt-3 d-flex align-items-center justify-content-center">
      <img src="https://images.unsplash.com/photo-1513094735237-8f2714d57c13?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=675&q=80"
      alt="" srcset="" class="mr-5 pr-5">
      <div class="d-flex flex-column mr-5 pr-5 mb-5 pb-5">
        <h2 class="display-6 mt-5 mb-5" style="font-size:26px; font-weight:bold">Login</h2>
            <form @submit.prevent="login">
                <div class="form-group">
                <input type="email" class="form-control pt-4 pb-4" placeholder="Email" v-model="loginData.email">
                <small class="form-text text-muted">We'll never share your email with anyone else.</small>
                </div>
                <div class="form-group">
                <input type="password" class="form-control pt-4 pb-4" placeholder="Password" v-model="loginData.password">
                </div>
                <div class="d-flex align-items-center">
                <button type="submit" class="btn btn-primary pt-3 pb-3 pr-4 pl-4 ">Log In</button>
                <router-link to="/register">
                    <button class='btn btn-link p-0 ml-3'>Sign Up Here</button>
                </router-link>
                </div>
            </form>
      </div>
      <loading-now v-if="nowLoading"></loading-now>
  </div>
</template>

<script>
import LoadingNow from '../components/LoadingNow'
export default {
  data () {
    return {
      loginData: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    login () {
      this.$store.dispatch('login', this.loginData)
        .then(_ => this.$router.push({ path: '/' }))
    }
  },
  computed: {
    nowLoading () {
      return this.$store.state.nowLoading
    }
  },
  components: {
    LoadingNow
  }
}
</script>

<style>
.cart {
    min-height: 88.4vh;
}

.cart img{
    height: 80vh;
}
</style>
