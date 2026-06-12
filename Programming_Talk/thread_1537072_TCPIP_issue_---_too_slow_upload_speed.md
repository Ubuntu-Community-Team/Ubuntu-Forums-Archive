---
title: "TCP/IP issue --- too slow upload speed"
date: 2010-07-23
forum: Programming Talk
---

### Post by kashyap_ankur on 2010-07-23
I am working on an  application --- which you can consider a simple/straight-forward  client-server thing. During the tests I discovered that while sending  large amount of data from client to server I never crossed 30 - 35 KBps  speed limit. In order to figure out if there is a problem with the  application or the connection, I tried to upload files by using attach  feature of multiple web-mail websites. In all the cases I noticed the  upload speed touching 80 - 90 KBps. Then it occurred to me that there  may be some problem with my server or at the server-side --- Virtual  instance of Ubuntu Server 9.04 on Amazon Cloud EC2. So I installed  Apache/PHP and created a simple file upload HTML page. Again, the upload  touched 80 - 90 KBps. So I was sure that the problem is either with my  sever app or the client app.

The server and client both are huge  applications, so I decided to write the simplest server and client and  then find out what's going wrong. I have attached the code of the server  with this email. To my disappointment --- I got the same poor results  --- 30 - 35 KBps. The client application is based on Windows using  Winsock 2. But all the application that showed 80 - 90 KBps are also  running on my Windows PC only. The code of the sample client isn't  attached with the email. The code is very simple. Create the socket,  connect, loop --- "send" Winsock 2 function call --- passing 4 KB of  data in each shot. Also tried different sizes --- 2/8 KB of data in each  shot.

I also tried changing the sizes of send and receive  buffers (SO_RCVBUF and SO_SNDBUF) to adjust the Window size, and I tried  this with both the client and server. No change in the results. I am  not sure where I am going wrong, at least so far as this simplest  application is concerned.

---

### Post by dwhitney67 on 2010-07-23
I took a look at your code; there doesn't seem to be anything that stands out.  However, I do not know what the value of BUFSIZ is declared to be.  You should avoid reading, that is calling read(), unless you know for a fact that there is actually data present on the socket.  You can use select() to determine when it is time to read.  Otherwise read() will block.

And personally, I would not call read(), but instead recv().  I realize that read() is essentially the same, but with no parameter for the option flag(s).


P.S.  A backlog of 128 for the listen() call??  Typically 5 should be sufficient.  If you expect a lot of connections, then handle each client in a separate thread.

---

