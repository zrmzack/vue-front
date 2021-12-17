<template>
  <div id="app">
    <el-form>
      <textarea v-model="key_value" placeholder="请输入问题" type="text"/>
      <textarea v-model="value_value" placeholder="请输入答案" type="text"/>
      <button @click="oncreate()">提交</button>
    </el-form>
  </div>
</template>
<script>
// eslint-disable-next-line no-unused-vars
import request from '@/views/redis/importConfig'

export default {
  name: 'Redis',
  data: function() {
    return {
      key_value: '',
      value_value: ''
    }
  },
  methods: {
    oncreate() {
      var tempx = this.key_value
      var tempy = this.value_value
      var newurl = '/redis/add/' + tempx.toString() + '/' + tempy.toString()
      console.log(newurl)
      request({
        method: 'POST',
        url: newurl
      })
      alert('redis存储成功')
    }

  }
}
</script>
