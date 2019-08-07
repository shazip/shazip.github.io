---
title: Keil生成自有库及使用
categories: 总结归纳
date: 2019-07-26 15:57:07
tags: 总结归纳

---



@[TOC](将模块打包成库)

# 生成一个库文件
为了程序逻辑清晰和保密的原因，有的程序会把有些功能打包成一个库文件以供使用，那么，怎么生成一个库文件呢？
1、需要相关功能的代码文件(.c和.h等)，这些文件需要能独立使用，不能包含该不存在的头文件和参数，与外部使用接口函数进行交互。
如下：准备代码文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726144828513.png)
实现一个加法功能，内容如下：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726145217115.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726145127505.png)

2、新建一个工程
选择芯片，必须选择才能编译
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726151607510.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)
3、右键project中的文件夹，选择Manage Components添加文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726151737435.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)
4、打开下图右上角Target 配置 魔术棒按键， 选择Output选项卡，勾选Create Library选项，
如果文件在不同的文件夹，需要在C/C++选项卡include paths中添加头文件路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019072615205961.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)
5、编译后就得到需要的.Lib文件了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726152833851.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)
# 使用库文件
生成库文件后我们使用是需要两种文件，一个是.lib文件，一个是.h文件
1、拿出一个野火的串口示例程序，将两个文件放进去，文件多可以单独弄个文件夹，但是需要添加头文件路径
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726154016557.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)
2、打开工程，将lib文件添加到工程中，就可以使用该库了
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726154313288.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)
3、使用，在使用前包含头文件就能直接调用库里的函数了。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190726155359923.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NoYXppcA==,size_16,color_FFFFFF,t_70)