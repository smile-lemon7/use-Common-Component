# use-Common-Component

描述： 该仓库是主项目，在该项目中使用了其他仓库中的子项目。

功能： 用来测试公共组件仓库提取、使用、修改、删除。

公共子模块处理

一、git submodule
1️⃣发布：公共组件单独写成一个项目。
步骤：
创建一个文件夹，手动生成package.json文件（npm init）。
正常写组件（不需要的目录删除）。
必须有index.js文件，将组件导出。
将写好的项目提交到远程git仓库中。
2️⃣使用：使用时用git submodule引入到主项目中。
在项目控制台中使用git submodule add <仓库地址> <本地路径>命令添加公共组件库。
名词解释： 仓库地址： 公共组件库的git地址。
     本地路径： 组件库需要克隆到该项目的哪个目录下，该路径不能是当前目录的已有路径。  
     通常是src/components/公共组件库名称。
然后在需要使用公共组件库的地方正常引入即可。
3️⃣修改：如果在本地修改了子模块，需要先提交子模块再提交主模块。
修改了子模块，cd到子模块的根目录，git status查看修改的文件。再正常add、commit。最后git push origin master即可。
提交主模块。
注意：主项目仓库不会保存子项目代码，保留的是子项目的commit id，用来唯一标识子项目的每一次提交。
4️⃣克隆：克隆一个带有公共组件库的项目
克隆下来不会直接带有组件库的代码，只是一个空文件夹和.gitmodules文件(用于记录子模块的路径以及远程版本库地址)。需要手动使用命令下载：git submodule update --init --recursive。
5️⃣更新：公共组件被修改时更新项目: git submodule foreach git pull
6️⃣删除组件库： git rm --cached common-component、rm -rf common-component、rm .gitmodules
