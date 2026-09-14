# Trials Survivors Save Editor

简体中文、单文件、纯前端的非官方 Trials Survivors 存档编辑器。`index.html` 内已包含全部样式和脚本，不需要安装 Node.js、配置服务器或加载外部 CDN。

## 首次开启 GitHub Pages

上传文件与启用 Pages 是两个独立步骤。本仓库按「从分支发布」准备，不需要自定义 Actions 工作流。

打开 [Settings → Pages](https://github.com/worsteggs/trials-survivors-save-editor/settings/pages)，在 **Build and deployment** 中设置：

- Source：**Deploy from a branch**
- Branch：**main**
- Folder：**/(root)**

点击 **Save**。查看仓库 Actions 中的 Pages 发布结果；成功后，Settings → Pages 会显示 **Visit site**。不要把文件存在或提交成功当作网站已经上线。

预期网站地址（仅在 Pages 成功发布后可用）：

https://worsteggs.github.io/trials-survivors-save-editor/

官方文档：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

`.nojekyll` 用于让 Pages 直接发布静态文件。后续更新 `main` 分支的 `index.html`，在发布来源保持上述配置时会触发重新发布。

## 使用

1. 完全退出游戏，独立备份整个存档目录。
2. ZIP 请先解压；网页当前接受单个/多个存档文件，或通过「选择整个存档目录」载入文件夹。
3. 修改需要的模块，下载当前文件。下载保持原文件名；若浏览器追加 `(1)`，替换前请恢复原名。
4. 将文件放回对应目录，保留未覆盖的原始备份。`.bak` 与主文件应区分处理；修改 `.bak` 不保证游戏会读取它。

也可以下载 `index.html`，在现代浏览器中直接打开离线使用。浏览器文件选择只是本地读取；编辑器没有存档上传接口，也没有内置个人存档。

## 已实现模块

职业等级/经验/解锁、全局成长、难度、地图、已发现技能 ID、成就统计、教程状态、当前 Run、Inventory 格子锁定状态，以及高级 JSON 编辑。

## 格式和边界

- 根据提供的样本识别普通 JSON 或循环 XOR JSON；XOR 字节为 `42 13 99 7A`，导出保持识别到的编码方式。
- 当前页面不直接导入 ZIP，也不批量导出整套目录。
- ID 是资源引用，界面无法证明一个手工填写的 ID 在游戏中存在。
- 空遗物/物品样本不足以确认新增对象结构，因此不凭空生成未知对象。
- JSON 解析与重新序列化可能改变数字的文本表示；这不是逐字节无损编辑器。JavaScript 大整数精度限制也应注意。
- 网页端解析/导出验证不等于经过所有游戏版本的实机加载验证。仅建议在自己的离线存档副本上测试，并始终保留可恢复的原始文件。

Unofficial community tool. Not affiliated with Angry Wisp.
