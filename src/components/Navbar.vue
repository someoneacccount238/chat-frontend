<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <router-link class="navbar-brand" to="#">{{ cookie }}</router-link>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item active">
                    <router-link class="nav-link" to="/messages">Messages</router-link>
                </li>

                <li class="nav-item" v-if="cookie">
                    <router-link class="nav-link" to='#' @click="logout">Logout</router-link>
                </li>
                <li class="nav-item" v-else-if="!cookie">
                    <router-link class="nav-link" to="/login" id="login">Login</router-link>
                </li>
                <li class="nav-item" v-if="!cookie">
                    <router-link class="nav-link" to="/signup" id="signup">Signup</router-link>
                </li>
            </ul>
        </div>
    </nav>
    <router-view />
</template>

<script> 

import { useCookies } from "vue3-cookies";
const { cookies } = useCookies();


export default {
    data() {

    },
    computed: {
        cookie() {
            return cookies.get('PHPSESSID');
        }
    },
    methods: {
        logout() {
            cookies.remove('PHPSESSID') 
            localStorage.removeItem("avatar");      
            localStorage.removeItem("email");
            location.reload();

        }
    },

    // mounted() {
    //     console.log({ router: this.$router });
    // }
} 
</script>
<style>
.navbar{
    position: absolute;
    top:0 !important;
}</style>