# Typora-0.11.18 最后一个免费版本

## Typora-0.11.18 The last free version

点击下载对应版本:

Click to download:

[![win64](https://img.shields.io/badge/Windows%20(64bit)-exe-blue)](https://github.com/zogodo/typora-0.11.18/raw/master/typora-setup-x64-0.11.18.exe)　[![win64](https://img.shields.io/badge/Windows%20(32bit)-exe-blue)](https://github.com/zogodo/typora-0.11.18/raw/master/typora-setup-ia32-0.11.18.exe)

[![win64](https://img.shields.io/badge/Linux%20(amd64)-deb-brightgreen)](https://github.com/zogodo/typora-0.11.18/raw/master/typora_0.11.18_amd64.deb)　[![win64](https://img.shields.io/badge/Linux%20(x64)-tar-brightgreen)](https://github.com/zogodo/typora-0.11.18/raw/master/Typora-linux-x64-0.11.18.tar.gz)　[![win64](https://img.shields.io/badge/Linux%20(arm64)-deb-brightgreen)](https://github.com/zogodo/typora-0.11.18/raw/master/typora_0.11.18_arm64.deb)

[![win64](https://img.shields.io/badge/MacOS-dmg-orange)](https://github.com/zogodo/typora-0.11.18/raw/master/Typora-0.11.18.dmg)

[Typora 最后免费版本也不能用了？简单一招搞定](https://xiaoniuhululu.com/2022-07-28_Typora_isExpired_deal/)

---



Typora 最后免费版本也不能用了？简单一招搞定
 发表于 2022-08-01
  更新于 2022-08-04
  分类于 百宝箱
  阅读次数： 1959


作者：小牛呼噜噜 | https://xiaoniuhululu.com
计算机内功、JAVA底层、面试相关资料等更多精彩文章在公众号「小牛呼噜噜 」

Typora是一款优秀的 Markdown 编辑器和阅读器

去年Typora还是免费的，今年的新版开始收费了，不过还是能理解的
当时摸了摸口袋



还是不选择升级了，就一直用的Typora-0.11.18版本，老就老一点吧，能用就行

公众号回复：Typora-0.11.18,即可获得最后免费版本Typora-0.11.18

但是最近发现最后的免费版本竟然也用不了，可能提前预知大家都不愿意升级 ，官方埋了个必须强制升级的雷，这个操作可太骚了！



检索了下目前网上主要这几种方式：

重新安装老版本，试了一下，还是这个强制升级的提示
修改系统时间可以，但是系统时间很重要，恢复正常时间还是不行，鸡肋
替换app.asar文件，搞了半天，也没效果，删了
使用网友给的winmm.dll，来爆破收费版本，没成功，网上不明安装包，还有点危险
没办法，好好地研究一下typora的注册表，一般权限都和注册表有点关系。

注册表其实就是软件安装在win系统里面的配置文件,弄了个好听的名字

先打开typora的注册表看看，里面是什么情况

打开注册表：按Windows+R打开运行窗口，输入 regedit
进入路径计算机\HKEY_CURRENT_USER\SOFTWARE\Typora


我们可以发现，里面竟然有个时间IDate，那岂不是我们把时间给改了，那就不过期了？ 赶紧试试
果然修改后发现再次打开Typora, 还是不行，但时间竟然还是恢复4/20/2022。不信了，再多试几次
好吧，还是这个结果


但也不是没有收获， 我们可以判断每次打开Typora，它会重置注册表中时间。那很有可能这个注册表里的时间 再加上当前系统时间来实现 Typora Beta强制过期的效果。不然Typora为什么会在启动时，一遍遍地重置这个注册表里的时间 呢？其中必有猫腻

笔者立刻就试试看：Typora不是每次打开都重置注册表里的时间， 那我们就阻止这种行为？我们通过修改当前系统用户权限，让其无权限修改该注册表！右键点击：计算机\HKEY_CURRENT_USER\SOFTWARE\Typora，权限，每个用户都拒绝。当然先要把IDate设置成未来的日期


我们再打开一下，神奇的一幕：


这样一下就解决问题了，还不需要下载额外的破解文件，分外优雅！


最后本文仅供学习参考之用，有条件的还是去支持一下正版
