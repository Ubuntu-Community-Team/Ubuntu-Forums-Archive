---
title: "checksum offload Qt4"
date: 2009-02-18
forum: Programming Talk
---

### Post by qbox on 2009-02-18
Hi
I write one application in Qt4
I have this code for making connection

```

clientSocket.abort();
	clientSocket.connectToHost(QHostAddress::LocalHost, 5555);

```

and I have this code for sending a packet:

```
	
	QByteArray block;
	QDataStream out(&block, QIODevice::WriteOnly);
	out.setVersion(QDataStream::Qt_4_0);
	out << (quint16)0;
	out << packet;
	out.device()->seek(0);
	out << (quint16)(block.size() - sizeof(quint16));

	clientSocket.write(block);
```

I scanning with wireshark to see if packet is send or not. The packet is send but in wireshark I see this error
```
 
Checksum: 0xfe3f [incorrect, should be 0x0865 (maybe caused by "TCP checksum offload"?)]
```
Probably the packed will be discarded on receiving. Any Idea what is this and how to make a packet with good check sum?

---

### Post by qbox on 2009-02-18
I try another quicker code

```
	QString message="AAAAAAAAAAAAAA";
	QByteArray msg = message.toUtf8();
	QByteArray block = "MESSAGE " + QByteArray::number(msg.size()) + " " + msg;
	clientSocket.write(block);
```

I still have same error and the packed is not discarded.
:popcorn:

---

