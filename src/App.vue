<template>
  <div>
    <h2>Rick and Morty api: 20 primeros personajes</h2>
    <div v-for="(character, index) of characters" :key="index" class="d-flex">
      <img :src="character.image" alt="" />
      <p>{{index+1}} {{ character.name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => {
    return {
      characters: [],
    };
  },
  created() {
    fetch(`https://rickandmortyapi.com/api/character`)
      .then((response) => {
        return response.json();
      })
      .then((data) => {
        this.characters = data["results"];
        // console.log(this.characters);
      });
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap");
body {
  font-family: "Orbitron", sans-serif;
  background-image: url('https://rickandmortypod.com/wp-content/uploads/2018/11/cropped-RM_page-header_background1-3.png');
  background-size: cover;
  background-repeat: no-repeat;
}
h2 {
  color: white;
  text-align: center;
}
img {
  border-radius: 50%;
  height: 150px;
}
.d-flex {
  display: flex;
  margin: 1em;
}
p {
  margin: auto 1em;
  color: green;
  font-weight: bolder;
  font-size: 1.5em;
}
</style>