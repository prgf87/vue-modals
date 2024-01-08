<template>
  <div>
    <h1>{{ title }}</h1>
  </div>
  <input type="text" ref="name" />
  <button @click="handleClick">Click</button>
  <teleport to="#modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#">Info</a>
      </template>
      <h1>Sign up for the Giveaway!</h1>
      <p>Grab our new merch for half the price!</p>
    </Modal>
  </teleport>
  <teleport to="#modals" v-if="showModalTwo">
    <Modal theme="" @close="toggleModalTwo">
      <h1>Verify your email</h1>
      <p>Go to your emails and click on the Verify Email link.</p>
    </Modal>
  </teleport>
  <p>Welcome!</p>
  <div>
    <button @click="toggleModal">Open Modal</button>
  </div>
  <div>
    <button @click="toggleModalTwo">Open 2nd Modal</button>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "My First Vue 3",
  components: { Modal },
  data() {
    return {
      title: "I am the TITLE",
      modal: {
        heading: "Sign up for the Giveaway!",
        text: "Grab our new merch for half the price!",
      },
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log("clicked", this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
#modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
/* h1 {
  display: inline-block;
} */
</style>
