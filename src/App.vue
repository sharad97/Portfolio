<template>
  <v-app>
    <v-navigation-drawer v-model="sidebar" app>
    <v-list>
    <div v-for="item in  menuItems">
        <router-link v-if="item.path" v-bind:to="item.path">
          <v-list-tile v-if="item.action" v-bind:key="item.title" @click="">
            <v-list-tile-action>
              <v-icon style="font-size:24px">{{ item.action }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{ item.title }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </router-link>
        <a v-else v-bind:href="item.link" target="_blank">
          <v-list-tile v-if="item.action" v-bind:key="item.title" @click="">
            <v-list-tile-action>
              <v-icon style="font-size:24px">{{ item.action }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{ item.title }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </a>
      </div>
      <v-toolbar-side-icon @click="sidebar = !sidebar">
              <v-icon style="font-size:24px">fa fa-times-circle</v-icon>
      </v-toolbar-side-icon>
    </v-list>
    </v-navigation-drawer>
    <v-toolbar app>
      <span class="hidden-sm-and-up">
        <v-toolbar-side-icon @click="sidebar = !sidebar">
          <v-icon style="font-size:24px">fa fa-bars</v-icon>
        </v-toolbar-side-icon>
      </span>
      <v-toolbar-items>
        <div>
        <v-btn flat color="purple">
        <router-link to="/" tag="span" style="cursor: pointer">
          <v-list-tile>
            <v-list-tile-action>
              <v-icon style="font-size:24px">fa fa-user-circle-o</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{ appTitle }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </router-link>
        </v-btn>
         </div>
      </v-toolbar-items>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <div v-for="item in  menuItems">
        <v-btn flat color="purple">
        <router-link v-if="item.path" v-bind:to="item.path">
          <v-list-tile v-if="item.action" v-bind:key="item.title" @click="">
            <v-list-tile-action>
              <v-icon style="font-size:24px">{{ item.action }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{ item.title }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </router-link>
        <a v-else v-bind:href="item.link" target="_blank">
          <v-list-tile v-if="item.action" v-bind:key="item.title" @click="">
            <v-list-tile-action>
              <v-icon style="font-size:24px">{{ item.action }}</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{ item.title }}</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </a>
        </v-btn>
      </div>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<style lang="scss">
@import './sass/app';
</style>

<style>
  @import 'https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css';
</style>

<script>
  export default {
    name: 'app',
    data () {
      return {
        sidebar: false,
        menuItems: [
          {
            action: 'fa-briefcase',
            title: 'Portfolio',
            path: '/Portfolio'
          },
          {
            action: 'fa fa-keyboard-o',
            title: 'Blog',
            path: '/Blog'
          },
          {
            action: 'fa-linkedin-square',
            title: 'LinkedIn',
            link: 'https://www.linkedin.com/in/sharadshrestha1/'
          },
          {
            action: 'fa-github-square',
            title: 'GitHub',
            link: 'https://github.com/sharad97'
          }
        ]
      }
    },
    computed: {
      appTitle () {
        return this.$store.state.appTitle
      }
    }
  }
</script>
