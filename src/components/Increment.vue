<!-- this example requires a modern browser that supports ES2015 natively -->

<script src="https://cdnjs.cloudflare.com/ajax/libs/deepstream.io-client-js/2.1.1/deepstream.js"></script>
<script src="https://unpkg.com/vue/dist/vue.js"></script>

<div id="app">
  <div class="group connectionState">
    Connection-State is: <em id="connection-state">{{connectionState}}</em>
  </div>
  <my-record :ds="ds"></my-record>
  <my-events :ds="ds"></my-events>
  <my-rpc :ds="ds"></my-rpc>
</div>

<template id="record-template">
  <div class="group realtimedb">
    <h2>Realtime Datastore</h2>
    <div class="input-group half left">
      <label>Firstname</label>
      <input type="text" v-model="firstname" @input="handleFirstNameUpdate()" />
    </div>
    <div class="input-group half">
      <label>Lastname</label>
      <input type="text" v-model="lastname" @input="handleLastNameUpdate()" />
    </div>
  </div>
</template>

<template id="events-template">
  <div class="group pubsub">
    <div class="half left">
      <h2>Publish</h2>
      <button class="half left" id="send-event" @click="handleClick()">Send test-event with</button>
      <input type="text" class="half" id="event-data" v-model="value"/>
    </div>
    <div class="half">
      <h2>Subscribe</h2>
      <ul id="events-received">
        <template v-for="event in eventsReceived">
          <li> {{event}} </li>
        </template>
      </ul>
    </div>
  </div>
</template>

<template id="rpc-template">
  <div class="group reqres">
    <div class="half left">
      <h2>Request</h2>
      <button class="half left" @click="handleClick()">Make multiply request</button>
      <div class="half">
        <input type="text" v-model="requestValue" class="half left" />
        <span class="response half item"> {{displayResponse}} </span>
      </div>
    </div>
    <div class="half">
      <h2>Response</h2>
      <div class="half left item">Multiply number with:</div>
      <input type="text" class="half" v-model="responseValue" />
    </div>
  </div>
</template>
