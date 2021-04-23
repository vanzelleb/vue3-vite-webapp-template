<template>
  <header :class="{ scroll: scrolled }">
    <div class="container">
      <h2><span>App name</span></h2>
    </div>
  </header>
</template>

<script>
import { onMounted, ref } from "vue";

export default {
  setup() {
    let scrolled = ref(false);

    const handleScroll = (e) => {
      scrolled.value = e.target.documentElement.scrollTop > 0;
    };

    onMounted(() => {
      window.addEventListener("scroll", handleScroll);
    });

    return {
      scrolled,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to component only -->
<style scoped>
header {
  padding: 12px 8px;
  position: -webkit-sticky;
  position: sticky;
  top: 0;
  background-color: white;
  z-index: 1;
}

span {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  margin: 0 0;
}

.container {
  display: flex;
  justify-content: center;
  max-width: 80ch;
  margin: 0 auto;
}

.scroll {
  -webkit-box-shadow: 0 3px 5px rgba(57, 63, 72, 0.3);
  -moz-box-shadow: 0 3px 5px rgba(57, 63, 72, 0.3);
  box-shadow: 0 3px 5px rgba(57, 63, 72, 0.3);
}
</style>
