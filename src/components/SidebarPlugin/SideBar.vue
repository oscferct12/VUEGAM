<template>
  <div class="sidebar">
    <div class="logo">
      <a href="#" class="simple-text logo-mini">
        <div class="logo-img">
          <img :src="imgLogo" alt>
        </div>
      </a>
      
      <a target="_blank" class="simple-text logo-normal">{{ title }}</a>
    </div>
    <dash-board></dash-board>
  </div>
</template>
<script>
import SidebarLink from "./SidebarLink.vue";
import DashBoard from "../../pages/Dashboard.vue";

export default {
  components: {
    SidebarLink,
    DashBoard
  },
  props: {
    title: {
      type: String,
      default: "GAM Project"
    },
    backgroundImage: {
      type: String,
      default: require("@/assets/img/sidebar-2.jpg")
    },
    imgLogo: {
      type: String,
      default: require("@/assets/img/logo.png")
    },
    activeColor: {
      type: String,
      default: "green",
      validator: value => {
        let acceptedValues = ["", "purple", "blue", "green", "orange", "red"];
        return acceptedValues.indexOf(value) !== -1;
      }
    },
    sidebarLinks: {
      type: Array,
      default: () => []
    },
    autoClose: {
      type: Boolean,
      default: true
    }
  },
  provide() {
    return {
      autoClose: this.autoClose
    };
  },
  computed: {
    sidebarStyle() {
      return {
        backgroundImage: `url(${this.backgroundImage})`
      };
    }
  }
};
</script>
<style>
@media screen and (min-width: 991px) {
  .nav-mobile-menu {
    display: none;
  }
}
</style>
