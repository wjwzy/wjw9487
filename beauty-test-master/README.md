# 预测颜值

# 项目所需要的环境：
python3.6及以上，keras2.2.4,face_recognition1.0.0
# 项目目录介绍：
prepare.py:数据预处理代码  
train.py:训练神经网络代码
static和templates文件夹下是实现前端的静态资源和页面代码
app.py:实现交互的核心部分  
注意将生成的h5文件放到model文件夹下

# 项目开发介绍：
本系统是基于深度学习八层的CNN集成python一个web框架flask开发而成的前后端分离系统。
该项目是基于Keras框架开发的项目，首先是数据集，是华南理工大学所制作的SCUT-FBP5500数据集，
它分为图片与标签，其中图片都是具有完整胸部以上的小半身人脸照，由各种各样的人组成，有中国人也有外国人。
标签文件是记事本格式，每一张图片对应一个颜值分数，分数从0到5之间。
在数据预处理阶段，我采用了常规操作裁剪、旋转与缩放至尺度为227×227。
在网络结构上，卷积通道使用了96个，大小为11*11步长为4不加边，激活函数用的是ReLU，
当然也包括了防止过拟合在三个全连接dense层之后dropout，loss函数用的是categorical_crossentropy。
基本都是一个图像分类问题该有的常规操作，最后保存训练epoch最好的model。
另外就是写一个web来方便操作测试单张图片的颜值，调用训练好的模型，
用JS语句给后端发送请求，调用写好的测试方法，就可以在前端页面进行颜值测试。
当然，还有一个关键的就是用到了识别脸部的开源库face_recognition。
