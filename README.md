> [!TIP]
>
> 现在可以有更好、更合适的选择：
>
> - ESLint - 代码质量检查
> - Prettier - 代码格式化
> - Stylelint - 样式格式化
>
> CSS 属性排序可以使用 stylelint + stylelint-order + [stylelint-config-recess-order](https://github.com/stormwarning/stylelint-config-recess-order)

# csscomb-mini (Deprecated)

初衷是使用 [CSScomb](https://github.com/csscomb/csscomb.js) 对小程序的样式文件进行格式化。

虽然 Prettier 已经做了很多格式化的事情，但 Prettier 不支持 CSS 属性的排序，所以本项目也是为了这个而创建的。

相关文章：

1. [将 CSScomb 集成到微信小程序项目中](https://github.com/tofrankie/blog/issues/128)
2. [将 CSScomb 集成到 Git Hook 中](https://github.com/tofrankie/blog/issues/129)

## 快速开始

```shell
# clone project
$ git clone git@github.com:tofrankie/csscomb-mini.git

# install dependencies
$ yarn

# format
$ yarn lint
```

配置

```json
{
  "scripts": {
    "csscomb:mini": "gulp csscombMini --path '<filepath>' --ext <extension>"
  }
}
```

- `--path` 表示符合 glob 文件匹配模式的路径，多个路径是用 `,` 隔开，并用单引号 `'` 括起来
- `--ext` 表示扩展名，如 `.css`、`.wxss` 等（此选项目前没什么用，保留下来后续优化用）

例如：

- 匹配所有 wxss 文件：`"gulp csscombMini --path './**/*.wxss'"`
- 匹配个别文件：`"gulp csscombMini --path 'miniprogram/app.wxss,miniprogram/pages/index/index.wxss'"`

## CSScomb 插件实现

详见 `gulpfile.js` 文件中的 `csscombPlugin` 方法。

## 其他

- [gulp-git-staged](https://www.npmjs.com/package/gulp-git-staged)

## TODO

- [ ] 当 gulp csscombMini 中不传参（path）时，是不处理，还是处理所有文件？
- [ ] 关于 CSScomb 在 VS Code 的配置可参考：[GentleHwang/csscomb-config-custom](https://github.com/GentleHwang/csscomb-config-custom)
