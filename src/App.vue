<template>
  <div id="app">
 
  <b-navbar toggleable="lg"  class = "nav-background">
    <b-navbar-brand href="#">NavBar</b-navbar-brand>

    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#">Link</b-nav-item>
        <b-nav-item href="#" disabled>Disabled</b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
          <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
        </b-nav-form>

        <b-nav-item-dropdown text="Lang" right>
          <b-dropdown-item href="#">EN</b-dropdown-item>
          <b-dropdown-item href="#">ES</b-dropdown-item>
          <b-dropdown-item href="#">RU</b-dropdown-item>
          <b-dropdown-item href="#">FA</b-dropdown-item>
        </b-nav-item-dropdown>

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template v-slot:button-content>
            <em>User</em>
          </template>
          <b-dropdown-item href="#">Profile</b-dropdown-item>
          <b-dropdown-item href="#">Sign Out</b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
<br>
<b-container>
  <b-row align-h="center" class = "mt-5">
    <b-col cols="5">
      <b-card class ="p-3">
        <h3 class = "mb-4">Login</h3>
      
       <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
      
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          required
          placeholder="Enter email"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

    

      <b-form-group id="input-group-4">
        <b-form-checkbox-group v-model="form.checked" id="checkboxes-4">
          <b-form-checkbox value="me">Remember me</b-form-checkbox>
      
        </b-form-checkbox-group>
      </b-form-group>
<div class = "d-flex justify-content-between">

<div>
      <b-button type="submit" variant="primary">Submit</b-button>&nbsp;
      <b-button type="reset" variant="danger">Reset</b-button>
      </div>
      <div>
        <a href="#" v-b-modal.modal1>Forgot Password</a>
      </div>
</div>
    </b-form>
      </b-card>
    </b-col>
    </b-row>
 
</b-container>

   

  </div>
</template>






<script>


export default {
  name: 'app',
  components: {

  },
  data(){
    return {
      showDismissibleAlert:false,
        form: {
          email: '',
          name: '',
          food: null,
          checked: []
        },
        foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
        show: true
      
    }
  },
  methods:{
    handleClick(){
     this.showDismissibleAlert =true;
    },
       onSubmit(evt) {
        evt.preventDefault();
        alert(JSON.stringify(this.form));
      },
      onReset(evt) {
        evt.preventDefault();
        // Reset our form values
        this.form.email = '';
        this.form.name = '';
        this.form.food = null;
        this.form.checked = [];
        // Trick to reset/clear native browser form validation state
        this.show = false;
        this.$nextTick(() => {
          this.show = true
        });
      }
  }
}
</script>




<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin:0;
  padding:0;
  background: #000000;

  padding-bottom:100px;
  width:100%;
  height: 100%;
  color:black;
}
.nav-background {
  background: gold;
  

}


</style>
