<!-- 
Copyright Amazon.com, Inc. or its affiliates. All Rights Reserved.
SPDX-License-Identifier: MIT-0 
-->
<template>
  <!-- Simple nav component used for global nav -->
  <nav
    class="navbar navbar-expand-lg navbar-light mb-5 justify-content-end"
    style="background-color: #FFA500;"
  >
    <div class="container">
      My Heron
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavAltMarkup"
        aria-controls="navbarNavAltMarkup"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
          <router-link class="nav-link active" to="/"
            ><i class="bi bi-house-door me-2"></i
          ></router-link>

          <router-link
            class="nav-link active"
            v-if="!isAuthenticated"
            to="/signin"
            ><i class="bi bi-box-arrow-in-right me-1"></i>Sign In</router-link
          >

          <router-link
            class="nav-link active"
            v-if="!isAuthenticated"
            to="/signup"
            ><i class="bi bi-person-circle me-2"></i>Sign up</router-link
          >

          <router-link
            class="nav-link active"
            v-if="isAuthenticated"
            to="/videos"
            ><i class="bi bi-camera-video-fill me-1"></i>Videos</router-link
          >


          <router-link
            class="nav-link active"
            v-if="isAuthenticated"
            to="/signals"
            ><i class="bi bi-broadcast me-1"></i>Signals</router-link
          >

          <router-link
            class="nav-link active"
            v-if="isAuthenticated"
            to="/integrations"
            ><i class="bi bi-arrow-left-right me-1"></i>Integrations</router-link
          >

          <router-link
            class="nav-link active"
            v-if="isAuthenticated"
            to="/qrcode"
            ><i class="bi bi-phone me-1"></i>App Configuration</router-link
          >

          <router-link
            class="nav-link active"
            v-if="isAuthenticated"
            to="/settings"
            ><i class="bi bi-gear me-1"></i>Settings</router-link
          >


          <router-link
            class="nav-link active"
            v-if="!isAuthenticated"
            to="/confirm"
            ><i class="bi bi-check-circle me-2"></i>Confirm Account</router-link
          >
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import { useStore } from "vuex";
import { computed } from "vue";
import { useRouter } from "vue-router";

export default {
  setup() {
    const router = useRouter();
    const store = useStore();

    async function logout() {
      store.dispatch("logout");

      router.push({
        name: "SignIn",
        params: { message: "You have logged out" },
      });
    }

    const isAuthenticated = computed(function() {
      return store.getters.isAuthenticated;
    });

    return {
      logout,
      isAuthenticated,
    };
  },
};
</script>

<style></style>
