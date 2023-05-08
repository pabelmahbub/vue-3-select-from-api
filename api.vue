<template>
  <div>
    <h2>Users</h2>
    <div>
      <label for="foodType">Food Type:</label>
      <v-select
        id="foodType"
        v-model="selectedFoodType"
        :options="foodTypes"
      ></v-select>
    </div>
    <div>
      <label for="country">Country:</label>
      <v-select
        id="country"
        v-model="selectedCountry"
        :options="countries"
      ></v-select>
    </div>
    <div>
      <label for="district">District:</label>
      <v-select
        id="district"
        v-model="selectedDistrict"
        :options="districts"
      ></v-select>
    </div>
    <button @click="displayData">Display Data</button>
    <ul v-if="displayUsers">
      <li v-for="user in filteredUsers" :key="user.id">
        <p>Name: {{ user.name }}</p>
        <p>Food Type: {{ user.foodType }}</p>
        <p>Country: {{ user.country }}</p>
        <p>District: {{ user.district }}</p>
        <p>projectName: {{ user.projectName }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import vSelect from 'vue-select'
import 'vue-select/dist/vue-select.css';

export default {
  components: {
    vSelect
  },
  data() {
    return {
      users: [
        { id: 1, name: "Aluino", foodType: "Swales", country: "japan", district: "Bigender", projectName:"LineOne" },
        { id: 2, name: "Ella", foodType: "Guitton", country: "Panama", district: "Female",projectName:"LineOne" },
        { id: 3, name: "Julina", foodType: "Tarbard", country: "USA", district: "Female",projectName:"LineOne" },
        { id: 4, name: "Walden", foodType: "McPhilip", country: "Brazil", district: "Male",projectName:"LineOne" },
        { id: 5, name: "Hillary", foodType: "Billingsley", country: "Norway", district: "Male",projectName:"LineThree" },
        { id: 6, name: "KKK", foodType: "McPhilip", country: "Brazil", district: "JJJ",projectName:"LineOne" },
        { id: 7, name: "LLL", foodType: "Billingsley", country: "Norway", district: "Male",projectName:"LineThree" }
      ],
      selectedFoodType: null,
      selectedCountry: null,
      selectedDistrict: null,
      displayUsers: false
    };
  },
  computed: {
    foodTypes() {
      return Array.from(new Set(this.users.map(user => user.foodType)));
    },
    countries() {
      return Array.from(new Set(this.users.map(user => user.country)));
    },
    districts() {
      return Array.from(new Set(this.users.map(user => user.district)));
    },
    filteredUsers() {
      let filtered = this.users;
      if (this.selectedFoodType) {
        filtered = filtered.filter(user => user.foodType === this.selectedFoodType);
      }
      if (this.selectedCountry) {
        filtered = filtered.filter(user => user.country === this.selectedCountry);
      }
      if (this.selectedDistrict) {
        filtered = filtered.filter(user => user.district === this.selectedDistrict);
      }
      return filtered;
    }
  },
  methods: {
    displayData() {
      this.displayUsers = true;
      console.log(this.displayUsers)
    }
  }
}
</script>

<style>

</style>
