<template>
  <div class="container">
    <form>
      <div class="row">
     <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
       <h1><b>VueJs Advanced Form</b></h1>
       <hr>
       <div class="form-group">
         <label for="email">Mail</label>
         <input 
                 type="text"
                 id="email"
                 class="form-control"
                 v-model="userData.email">
       </div>
        <div class="form-group">
         <label for="password">Password</label>
         <input 
                 type="password"
                 id="password"
                 class="form-control"
                 v-model="userData.password">
       </div>
        <div class="form-group">
         <label for="age">Age</label>
         <input 
                 type="number"
                 id="age"
                 class="form-control"
                 v-model="userData.age">
       </div>
     </div>
      </div>
      <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
        <label for="message">message</label><br>
        <!-- Interpolation between <textarea> {{ test }} </textarea> doesn't work!-->
        <textarea 
                   id="message"
                   rows="5"
                   class="form-control"
                   v-model="userData.message"> </textarea>
      </div>
      </div>
      <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="form-group">
        <label for="sendmail">
          <input
                 type="checkbox"
                 id="sendmail"
                 value="SendMail"
                 v-model="sendMail"> SendMail
        </label>
        <label for="sendInfomail">
            <input 
                    type="checkbox"
                    id="sendInfomail"
                    value="SendInfoMail"
                    v-model="sendMail"> SendInfoMail

        </label>   
        </div>
      </div>
      </div>
       <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
        <label for="male">
          <input
                 type="radio"
                 id="male"
                 value="Male"
                 v-model="gender"> Male
        </label>
        <label for="female">
            <input 
                    type="radio"
                    id="female"
                    value="Female"
                    v-model="gender"> Female

        </label>   
        </div>
      </div>
     <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
        <label for="priority"> Priority </label>
          <select
                 id="priority"
                 class="form-control"
                 v-model="selectedPriority">
                 <option v-for="priority in priorities" :key="priority.index">{{priority}}</option>
          </select> 
        </div>
      </div>
     <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
        <app-switch v-model="dataSwitch"></app-switch>
        </div>
      </div>
      <hr>
      <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <button 
                 class="btn btn-primary"
                   @click.prevent="submited">  Submit
        </button>
      </div>
      </div>
    </form>
    <hr>
    <div class="row" v-if="isSubmited">
       <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
         <div class="panel panel-default">
           <div class="panel-heading">
             <h4>Your Data</h4>
         </div>
         <div class="panel-body">
           <p><strong>Mail:</strong> {{ userData.email }}</p>
           <p><strong>Password:</strong>{{ userData.password }}</p>
           <p><strong>Age:</strong>{{ userData.age }}</p>
           <p style="white-space: pre"><strong>Message:{{ userData.message }}</strong></p>
           <p><strong>Send Mail?:</strong></p>
           <ul>
             <li v-for="item in sendMail" :key="item.index">{{item }}</li>
           </ul>
           <p><strong>Gender:</strong>{{gender}}</p>
           <p><strong>Priority:</strong>{{selectedPriority}}</p>
            <p><strong>Switched:</strong>{{dataSwitch}}</p>
         </div>
       </div>
    </div>
  </div>
  </div>
</template>

<script>
import Switch from './component/switch'
export default {
 data(){
   return{
     userData: {
        email: '',
        password: '',
        age: 18,
        message: 'This the first Message.',
     },
     sendMail: [],
     gender: 'Male',
     selectedPriority: 'Medium',
     priorities: ['High', 'Medium', 'Low'],
     dataSwitch: true,

     isSubmited: false,
     
   }
 },
 methods: {
   submited(){
     return this.isSubmited = true;
   }
 },
 components: {
   'app-switch': Switch,
 }
}
</script>

<style>

</style>
