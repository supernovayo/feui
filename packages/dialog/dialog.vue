<template>
  <div v-show="this.value">
    <div class="weui-mask"></div>
    <div class="weui-dialog" :class="{ 'weui-skin_android': skin === 'android' }">
      <div class="weui-dialog__hd" v-if="title"><strong class="weui-dialog__title" v-html="title"></strong></div>
      <div class="weui-dialog__bd" v-html="message"></div>
      <div class="weui-dialog__ft">
        <a class="weui-dialog__btn weui-dialog__btn_default" v-if="showCancelButton"
           @click="handleAction('cancel')" v-text="cancelButtonText"></a>
        <a class="weui-dialog__btn weui-dialog__btn_primary" v-if="showConfirmButton"
           @click="handleAction('confirm')" v-text="confirmButtonText"></a>
      </div>
    </div>
  </div>
</template>

<script>
 
  export default {
    name: 'fe-dialog',
    props: {
      skin: String,
      title: String,
      message: String,
      beforeClose: Function,
      confirmButtonText: String,
      cancelButtonText: String,
      showConfirmButton: {
        type: Boolean,
        default: true
      },
      showCancelButton: {
        type: Boolean,
        default: false
      },
    },

    data () {
      return {
        value: false
      }
    },

    methods: {
      handleAction (action) {
        this.value = false;
        let callback = this.callback
        callback(action)
      }
    }
  }
</script>
