<template>
  <div>
    <h1 v-dynamic="messageAsHTML"></h1>
  </div>
</template>
<script>
import Vue from "vue";
export default {
  directives: {
    dynamic: function(el, bind, vnode) {
      el.innerHTML = bind.value;
    }
  },
  data() {
    return {
      message: "THURSDAY"
    };
  },
  computed: {
    messageAsHTML: function() {
      return this.message.replace(/([^\x00-\x80]|\w)/g, "<span>$&</span>");
    }
  },
  mounted() {
    const letters = this.$el.getElementsByTagName("span");
    Array.from(letters, mappingFunction);

    function mappingFunction(l, i) {
      l.style['color'] = "green";
      l.style['opacity'] = "0.5";
    }
  }
};
</script>
<style scoped>
div {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 500px;
  background-color: rgb(26, 26, 26);
}
h1 {
  font-weight: 900;
  font-size: 3.5em;
  color: inherit;
  position: relative;
  display: inline-block;
  line-height: 1em;
}

h1::before {
  content: "";
  position: absolute;
  top: -10px;
  left: 0;
  width: 100%;
  height: 5px;
  background-color: aliceblue;
}

h1::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 5px;
  background-color: aliceblue;
}

.letter {
  color: green;
}
</style>

