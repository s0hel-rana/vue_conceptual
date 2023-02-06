<template>
  <div id="header">
    <div class="menu">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <router-link :to="{name:'Contact'}">Contact</router-link>
    </div>
    <div class="list">
      <span v-for="(id,index) in userIds" :key="index">
        <router-link :to="{name:'Profile', params:{user_id:id} }">Profile :{{ id }}</router-link>
      </span>
    </div>
    <button @click="Home">Home</button>
    <button @click="About">About</button>
    <button @click="Contact">Contact</button>
    <button @click="Back">Back</button>
    <button @click="Forward">Forward</button>
  </div>
</template>

<script>

export default {
  name: 'Header',
  data(){
    return{
      userIds: ['1','2','3','4','5']
    }
  },
  methods:{
    Home(){
      this.$router.push({name:'Home'})
    },
    About(){
      this.$router.push({name:'About'})
    },
    Contact(){
      this.$router.push({name:'Contact'})
    },
    Back(){
      this.$router.go(-1)
    },
    Forward(){
      this.$router.go(1)
    }
  }
}
</script>

<style>
  *{
        box-sizing: border-box;
    }
    .menu{
        background-color: green;
        display: flex;
        justify-content: flex-end;
    }
    .menu a{
        text-decoration: none;
        padding: 20px;
        font-size: 19px;
    }

    a.router-link-exact-active{
      color: red;
    }
    .list{
      background: rgb(196, 196, 190);
      display: flex;
      justify-content: flex-end;
    }
    .list a{
      text-decoration: none;
      padding: 15px;
      font-size: 15px;
    }
    button{
      background: green;
      padding: 8px;
      margin-top: 5px;
      color: white;
      border: 1px solid green;
      border-radius: 4px;
    }
    @media screen and (max-width:900px) {
        .menu{
            flex-direction: column;
            padding: 10px;

        }
        .menu a{
            background-color: rgb(43, 128, 226);
            margin: 10px 0;
            text-align: center;
            border-radius: 10px;
        }
      }

</style>
