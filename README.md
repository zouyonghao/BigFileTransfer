# BigFileTransfer
利用Netty进行大文件传输(zero-copy)

使用Netty自带的ChunkedWriteHandler在客户端和服务器之间传输超大文件

write()方法，将数据包装成PendingWrite塞入发送队列

flush()方法，从发送队列取出数据（如果是ChunkedInput类型的数据，同时根据isEndOfInput()方法，判断stream中是否还有数据），
将其发送到对应的channel中，该过程如果发生阻塞，通过注册监听以及channelWritabilityChanged()方法在通道可写的情况下继续发送。

>该项目操作流程：
1. 开启服务端(FileUploadServer)
2. 开启客户端(FileUploadClient)，完成与服务端连接
3. 从客户端输入文件路径，完成从client->server的文件发送

有问题可以联系zhangjimic@outlook.com交流学习
