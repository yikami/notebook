## [splitChunksPlugin](https://www.webpackjs.com/plugins/split-chunks-plugin/)
> 数据分块不放在一个js文件里，方便更新代码的时候不重新编译所有依赖

### webpack 自动分割块的条件
- node_modules中的模块
- 模块大于30kb
- 当按需加载块时，并行请求的最大数量将小于或等于5
- 在初始页面加载时并行请求的最大数量将小于或等于3

### 当满足所有条件时，来自相同块和缓存组的模块将形成一个新的块。
- minSize (默认值:30000)。
- minChunks(默认值:1)分割前共享模块的最小块数
- maxInitialRequests(默认为3)入口点上并行请求的最大数量
- maxAsyncRequests(默认为5)按需加载时并行请求的最大数量

### 默认配置
```
splitChunks: {
    chunks: "async",
    minSize: 30000,
    minChunks: 1,
    maxAsyncRequests: 5,
    maxInitialRequests: 3,
    automaticNameDelimiter: '~',
    name: true,
    cacheGroups: {
        vendors: {
            test: /[\\/]node_modules[\\/]/,
            priority: -10
        },
    default: {
            minChunks: 2,
            priority: -20,
            reuseExistingChunk: true
        }
    }
}
```