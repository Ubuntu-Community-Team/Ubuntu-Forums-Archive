---
title: "Socket programming"
date: 2012-12-10
forum: Programming Talk
---

### Post by sanda199 on 2012-12-10
hi everyone, i just wanna know how to connect 2 computers with socket programming in c language. Both of computers are using ubuntu OS. thanks

---

### Post by SuperCamel on 2012-12-10
Google for 'POSIX socket API'.

---

### Post by sanda199 on 2012-12-10
I know how to connect client and server in one computer which is running ubuntu OS. But I dun know how to connect in different computer. Pls help me... Thanks :)

---

### Post by bird1500 on 2012-12-10
The best tutorial I found online is [this one]("http://beej.us/guide/bgnet/").
It teaches the latest IPv6 standard (with all the bells and whistles, including sockets) and it's slightly funny, which is good.

Other resources I found are typically either too small or too professorial and bloated, or outdated.

EDIT: to connect 2 different computers you need to know the other computer's IP and use it to create a socket to connect to it.

---

### Post by sanda199 on 2012-12-10
But there is router between 2 computers. So IP address of both computers will be the same right?

---

### Post by bird1500 on 2012-12-10
I don't know, but I suspect that from the perspective of your computer the other one will have 2 IP addresses, the local one (typically 192.x.x.x or other ones alike) and the public one, which is the one which all [internet websites detect]("http://whatismyipaddress.com/") when you visit them.

All I know is that the IP/http/dns/router/IP mask/whatever stacks are incredibly complex and you have to read entire books to clearly get the whole picture.

---

### Post by sanda199 on 2012-12-17
hi, i am a newbie for ubuntu. I would like to know that how to connect 2 ubuntu computers by using TCP/IP socket programming. If anyone knows, pls share me some knowledge. I'm really appreciate your help.

---

### Post by dwhitney67 on 2012-12-17
[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by lisati on 2012-12-19
Threads merged. Please do not start multiple threads for the same question, it dilutes the community's ability to help.

---

