<template>
  <div class="hello">
    <button v-on:click='playAudio'>Music</button>
  </div>
</template>

<script>
const someSound = require("../audios/keyboard.mp3"); // require the sound

export default {
  name: "Audio",
  data: () => ({
    // you can access to the sound with this.someSound
    // same as someSound: someSound
    someSound
  }),
  methods: {
    // Selects a note
    // This method doesn't add value to the component, you can use
    // this.someSound directly
    getAudio() {
      return this.someSound;
    },

    playAudio() {
      // Plays a note, selected via getNote()
      //let note = new Audio(this.getNote()); // or
      let audio = new Audio(this.someSound);
      // note.play(); // new Audio will load asynchronously the audio
      // so instead of play directly after create note, you can listen for
      // a event and wait for it to know that the sound was loaded and can be
      // played

      // listen for the canplaythrough event
      audio.addEventListener("canplaythrough", () => {
        /* the audio is now playable; play it if permissions allow */
        audio.play(); // the audio now can be played
      });
    }
  }
};
</script>

<style scoped>

</style>