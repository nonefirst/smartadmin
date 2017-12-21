# element ui 2升级注意事项：
1.  卸载1.x升级到2以上，会发现console发生大量的报错，需要把vue、vue-compile-template升级到最新版本即可（目前是2.5.9）
2.  新版本的icon使用方式发生改变，需要注意如何使用的
3.  dialog的v-model方式改为:visible.sync 并且支持了按钮放到footer的方式




# webpack 1升级到3升级列表（element ui仍然是1的时候）
1.  首先使用vue init创建一个包含webpack3的项目，把build下的配置全部拷贝进来
2.  resolve.alis直接拷贝进来
3.  loader对比下拷贝进来
4.  压缩组件暂时不拷贝进来，老的估计有新替换方案
5.  webpack.dev.conf.js下的new HtmlWebpackPlugin({下的favicon拷贝进来
6.  新增组件：friendly-errors-webpack-plugin、webpack-dev-server、chalk、copy-webpack-plugin、webpack-bundle-analyzer、node-notifier、postcss-import、postcss-loader、semver、optimize-css-assets-webpack-plugin、rimraf、portfinder、vue-loader、vue、vue-template-compile、css-loader、style-loader、autoprefixer
7.  babel-loader需要升级到最新版本
8.  sass-loader需要升级到最新版本
9.  node-sass需要升级到最新版本
10. babel-preset-es2015需要被替换成babel-preset-env，并且.babel文件里面的es2015需要改为env
11. isparta-loader需要改为istanbul-instrumenter-loader
12. package.json中的script脚本变更：
        "scripts": {
            "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js",
            "start": "npm run dev",
            "build": "node build/build.js"
        },
13. element ui会发生报错找postcss-config.js的问题，需要再根目录增加postcss.config.js文件，内容为：
        module.exports = {
            plugins: [require('autoprefixer')()]
        }
14. sinon跟chalk两个组件也升级，否则npm list的时候会有提示
15. config/index.js下的build的assetsPublicPath: './resource/',需要设置下，否则build后路径对不上
以上的升级基本可以保证原系统能正常运行，前台界面仍然有大量报错，需要继续修改。
