<template>
<v-container>
    <braner></braner>
    <v-row>
<v-col xs=12 md=4
        v-for="(article, i) in articles"
        :key="i"
        >
  <v-card  
    class="mx-auto"
    max-width="400"
  >
    <v-img
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>{{article.title_heading}}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">{{article.title_description}}</v-card-subtitle>

    <v-card-text class="text--primary">
      <div>{{article.shot_content}}</div>

      <div>Whitsunday Island, Whitsunday Islands</div>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="orange"
        text
      >
        Share
      </v-btn>

      <v-btn
        color="orange"
        text
      >
        Explore
      </v-btn>
    </v-card-actions>
  </v-card>
  </v-col>
  </v-row>
  </v-container>
</template>

<script>
import braner from '../components/braner.vue'
import axios from 'axios'
export default {

     components: {
    braner,
  },

    data: () => ({

         articles: []
    }),

    mounted(){
    this.getData();
  },
  methods:{
    getData: async function() {
      let xdata;
      let url = process.env.VUE_APP_DATAAPI
      
      xdata = await axios.get(url+'contents')
      this.articles = xdata.data
      // console.log(xdata)
    } 
  },
  computed: {
      ximage() {
      return process.env.VUE_APP_IMGHOST+this.article.himage.url
       //return 'http://172.18.1.75:1337/uploads/sea_turtle_camp_and_crocodile_adventure5_451a4f11bd.jpg';
    },
    },
}
</script>