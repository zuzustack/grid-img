<template>
  <div>
    <h2>Image Grid</h2>

    <div>
      <input
        @keyup.enter="addImages"
        ref="data"
        type="text"
        v-model="text"
        id="data"
        style="margin-bottom: 2rem"
      />
      <button @click="addImages" type="submit">Add</button>

      <div class="grid">
        <div
          @click="deleteImg(index)"
          class="border"
          v-for="(img, index) in images"
        >
          <p class="text-box">Delete</p>
          <img :src="`https://source.unsplash.com/800x800?${img}`" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [],
      text: "",
    };
  },

  methods: {
    addImages() {
      if (this.images.length < 10) {
        this.images.push(this.text);
        this.text = "";
        this.$refs.data.focus();
      }
    },

    deleteImg(index) {
      this.images.splice(index, 1);
    },
  },

  mounted() {
    this.$refs.data.focus();
  },
};
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

.grid {
  justify-content: center;
  margin-inline: auto;
  width: 100%;
  max-width: 800px;
  display: flex;
  flex-wrap: wrap;
}

.text-box {
  cursor: pointer;
  width: 150px;
  transition: 0.3s;
  display: grid;
  place-content: center;
  margin: 0;
  background: #0000009b;
  color: azure;
  position: absolute;
  height: 0px;
  overflow: hidden;
}

.border:hover .text-box {
  height: 150px;
  width: 150px;
}

.grid img {
  background-color: rgba(0, 0, 0, 0.318);
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
  width: 150px;
  height: 150px;
}
</style>
