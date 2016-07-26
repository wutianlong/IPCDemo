# IPCDemo
Android IPC demo,  and  messenger implements IPC

参考文章：http://blog.csdn.net/luoyanglizi/article/details/51980630

# AIDL 基本语法
1。 文件类型：用AIDL书写的文件的后缀是 .aidl，而不是 .java。


2。 数据类型：AIDL默认支持一些数据类型，在使用这些数据类型的时候是不需要导包的，但是除了这些类型之外的数据类型，在使用之前必须导包，就算目标文件与当前正在编写的 .aidl 文件在同一个包下——在 Java 中，这种情况是不需要导包的。比如，现在我们编写了两个文件，一个叫做 Book.java ，另一个叫做 BookManager.aidl，它们都在 com.lypeer.aidldemo 包下 ，现在我们需要在 .aidl 文件里使用 Book 对象，那么我们就必须在 .aidl 文件里面写上 import com.lypeer.aidldemo.Book; 哪怕 .java 文件和 .aidl 文件就在一个包下。 
默认支持的数据类型包括： 
Java中的八种基本数据类型，包括 byte，short，int，long，float，double，boolean，char。
String 类型。
CharSequence类型。
List类型：List中的所有元素必须是AIDL支持的类型之一，或者是一个其他AIDL生成的接口，或者是定义的parcelable（下文关于这个会有详解）。List可以使用泛型。
Map类型：Map中的所有元素必须是AIDL支持的类型之一，或者是一个其他AIDL生成的接口，或者是定义的parcelable。Map是不支持泛型的。


3。 定向tag：这是一个极易被忽略的点——这里的“被忽略”指的不是大家都不知道，而是很少人会正确的使用它。在我的理解里，定向 tag 是这样的：AIDL中的定向 tag 表示了在跨进程通信中数据的流向，其中 in 表示数据只能由客户端流向服务端， out 表示数据只能由服务端流向客户端，而 inout 则表示数据可在服务端与客户端之间双向流通。其中，数据流向是针对在客户端中的那个传入方法的对象而言的。in 为定向 tag 的话表现为服务端将会接收到一个那个对象的完整数据，但是客户端的那个对象不会因为服务端对传参的修改而发生变动；out 的话表现为服务端将会接收到那个对象的的空对象，但是在服务端对接收到的空对象有任何修改之后客户端将会同步变动；inout 为定向 tag 的情况下，服务端将会接收到客户端传来对象的完整信息，并且客户端将会同步服务端对该对象的任何变动
