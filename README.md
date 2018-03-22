# vue-slip-delete
<p>
  <a href="https://www.npmjs.com/package/vue-slip-delete"><img src="https://img.shields.io/npm/dm/vue-slip-delete.svg" alt="Downloads"></a>
  <a href="https://www.npmjs.com/package/vue-slip-delete"><img src="https://img.shields.io/npm/v/vue-slip-delete.svg" alt="Version"></a>
</p>

vue left slip，左滑删除组件

# usage
```
npm install vue-slip-delete --save
```

```vue
<template>
  <slip-del
    v-for="(item, i) in list"
    :key="i"
    ref="slipDel"
    del-text="删除商品"
    @slip-open="slipOpen"
    @del-click="del"
  >
    <div slot="item" class="demo-item">delete item</div>
  </slip-del>
</template>

<script>  
import SlipDel from 'vue-slip-delete'

export default {
  methods: {
    slipOpen(target) {
      // 滑开一个删除，其他删除都关闭
      this.$refs.slipDel.forEach(item => {
        if (item.$el !== target.parentNode) {
          item.setOpen(false)
        }
      })
    },
    del() {
      // 删除回调
    }
  },
  components: {
    SlipDel
  }
}
</script>
```
# feature
- [x] 滑动角度判断
- [x] 滑动结束回调

# props  
名称|类型|默认值|描述
----|----|----|----
threshold|Number|35|滑动的阀值
del-cls|String|m-slide__del-red|删除按钮的类名
del-text|String|删除|删除文案 

# event
名称|描述
----|----
del-click|点击删除的回调
slip-open|滑动打开后的回调

# method
名称|描述
----|----
setOpen|打开或关闭 删除

# demo

<img src="./src/assets/demo.png" width="300px">

