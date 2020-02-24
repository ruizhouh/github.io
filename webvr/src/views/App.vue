<template>
    <div id="app">
        <!--    <img alt="Vue logo" src="../assets/logo.png">-->
<!--        <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    </div>
</template>


<script>
// import HelloWorld from '../components/HelloWorld.vue'
import * as Three from 'three'
import WebVR from '@/js/WebVR'

var scene = new Three.Scene();
var camera = new Three.PerspectiveCamera(45,window.innerWidth/window.innerHeight,1,1000)
var renderer = new Three.WebGLRenderer();
renderer.setSize(window.innerWidth,window.innerHeight);
document.body.appendChild(renderer.domElement);

var geometry = new Three.BoxGeometry(1,1,1);
var material = new Three.MeshBasicMaterial({color:0xec7259});
var cube = new Three.Mesh(geometry,material);
scene.add(cube);

camera.position.z = 20;
document.body.appendChild( WebVR.createButton(renderer) );
// renderer.xr.enabled=true;
renderer.vr.enabled=true;

renderer.setAnimationLoop( function () {

    renderer.render( scene, camera );

} );
// function render() {
//   requestAnimationFrame( render );
//   cube.rotation.x += 0.1;
//   cube.rotation.y += 0.1;
//   renderer.render( scene, camera );
// }
// render();

export default {
  name: 'App',
  components: {
    // HelloWorld
  }
}
</script>

<style>
#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;*/
  /*-webkit-font-smoothing: antialiased;*/
  /*-moz-osx-font-smoothing: grayscale;*/
  /*text-align: center;*/
  /*color: #2c3e50;*/
  /*margin-top: 60px;*/
}
</style>
