# eclipse-offine-plugin
需要在无网路环境中使用Eclipse，但是Eclipse常用的插件需要联网进行下载安装，官方没有直接提供插件离线包的下载。经过一顿搜索，发现了插件离线包制作的方法，在此记录下并存一些常用的插件离线包。

## 制作步骤
1. 在[Eclipse Marketplace插件市场](https://marketplace.eclipse.org/)搜索想要制作离线包的插件。
2. 找到插件的`Update site url`。
3. 在本地新建一个文件夹，用于存放插件离线相关文件。
4. 执行以下两条命令，提取插件的离线文件。
   ```shell
   eclipsec.exe -nosplash -application org.eclipse.equinox.p2.metadata.repository.mirrorApplication -source [步骤2中的Update site url] -destination file:///[步骤3中的本地文件夹绝对路径]
   eclipsec.exe -nosplash -application org.eclipse.equinox.p2.artifact.repository.mirrorApplication -source [步骤2中的Update site url] -destination file:///[步骤3中的本地文件夹绝对路径]
   ```
   特别说明：`eclipsec.exe`位于`eclipse`目录(即从[Eclipse官网](https://www.eclipse.org/downloads/packages/)下载eclipse的压缩包后的解压后目录)下，上面的命令中，`eclipsec.exe`可以替换为绝对路径，比如`D:/eclipse/eclipsec.exe`。
5. 将本地插件离线相关文件所在的文件夹压缩为`.zip`压缩包。
6. 制作完成后就可以将`.zip`压缩包通用U盘等方式拿到无网络环境使用eclipse进行离线安装啦。

## 示例
以制作`Darkest Dark Theme with DevStyle`插件离线安装包为例：
1. 在[Eclipse Marketplace插件市场](https://marketplace.eclipse.org/)搜索`Darkest Dark Theme with DevStyle`插件
   ![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/d440c908-9a7f-4a9c-99ab-97aeecf5cbd3)

2. 找到插件的`Update site url`并记录：`https://www.genuitec.com/updates/devstyle/ci/`
   ![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/e0563575-0430-4ce6-acd3-e9e4e5d36a8b)

3. 在D盘新建目录`Darkest_Dark_Theme_with_DevStyle`，绝对路径为`D:/Darkest_Dark_Theme_with_DevStyle/`
4. 进入`Darkest_Dark_Theme_with_DevStyle`目录，鼠标右键选择`在终端中打开`，在此路径下打开命令行终端
5. 执行命令，提取`Darkest_Dark_Theme_with_DevStyle`的离线文件
   命令1：
   ```shell
   E:/app2/eclipse/eclipsec.exe -nosplash -application org.eclipse.equinox.p2.metadata.repository.mirrorApplication -source https://www.genuitec.com/updates/devstyle/ci/ -destination file:///D:/Darkest_Dark_Theme_with_DevStyle/
   ```
   命令1执行命令行的结果：<br>
   ![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/54af125d-d518-450f-830c-707e117965a4)

   命令1执行后的文件内容：<br>
   ![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/9fdf426b-e6d3-445b-a418-433b92f864d2)

   命令2：
   ```shell
   E:/app2/eclipse/eclipsec.exe -nosplash -application org.eclipse.equinox.p2.metadata.repository.mirrorApplication -source https://www.genuitec.com/updates/devstyle/ci/ -destination file:///D:/Darkest_Dark_Theme_with_DevStyle/
   ```
   
   命令2执行后的执行结果：<br>
   ![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/4ab217c8-b921-422f-be51-23f32d60c13c)

   命令2执行后的文件内容：<br>
   ![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/5c70778e-abcd-4916-a69c-6b57c7be9f4a)

6. 打包压缩，收工。![image](https://github.com/suheng1921/eclipse-offine-plugin/assets/85484756/5e6bc22a-0e5d-4102-90c8-b780e6a9b276)


## 参考链接
1. [Equinox p2 Repository Mirroring](https://wiki.eclipse.org/Equinox_p2_Repository_Mirroring)
2. [How to download eclipse marketplace plugins for offline install](https://stackoverflow.com/questions/70746838/how-to-download-eclipse-marketplace-plugins-for-offline-install)

