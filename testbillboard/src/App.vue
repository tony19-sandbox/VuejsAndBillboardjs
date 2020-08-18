<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div ref="chart"></div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import bb, { line, areaSpline } from 'billboard.js';

@Component
export default class App extends Vue {
  async mounted() {
    await this.$nextTick();
    bb.generate({
      bindto: this.$refs.chart,
      data: {
        columns: [
          ['data1', 30, 200, 100, 170, 150, 250],
        ],
        types: {
          data1: line(),
          data2: areaSpline(),
        },
        colors: {
          data1: 'red',
          data2: 'green',
        },
      },
    });
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
