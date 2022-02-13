<template>
<v-container>
  <br>
  <center><h1>Homework / Asssignment</h1></center>
  <br>
  <v-row justify="center">
      <v-col
        cols="12"
        sm="10"
        md="8"
        lg="6"
        
      >
  <v-form ref="form" v-model="valid" lazy-validation >
    <v-select
      v-model="dataList.subject"
      :items="items1"
      :rules="[(v) => !!v || 'Item is required']"
      label="Subject"
      required
    ></v-select>
    <v-row
    justify="center"
    align="center"
    
  >
    <v-btn :disabled="!valid" color="amber darken-1"  @click="save" width="100">
      ADD
    </v-btn>
  </v-row>
    <br>
    <br>
    
  </v-form>
    </v-col>
</v-row>

  <v-card max-width="500" class="mx-auto">
    <v-toolbar color="brown darken-2" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>To do</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
    <v-list>
      <v-list-item v-for="(item,index) in List" :key="index">
        <v-list-item-content>
          <v-list-item-title v-text="item.name"></v-list-item-title>
        </v-list-item-content>
        <v-btn @click="Del(index)" color="pink lighten-2">Delete</v-btn>
      </v-list-item>
    </v-list>
  </v-card>
</v-container>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    dataList: {
      subject: "",
    },
    List: [
      {
        name: "Subject",
      },
    ],
    items1: ["Subject#1", "Subject#2", "Subject#3", "Subject#4"],
  }),
  methods: {
    save() {
      this.List.push({
        name: this.dataList.subject,
      });
    },
    Del(n){
        this.List.splice(n,1);
        }
  },
};
</script>

<style></style>
