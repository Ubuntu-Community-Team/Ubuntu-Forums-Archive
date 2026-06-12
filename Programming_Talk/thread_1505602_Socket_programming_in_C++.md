---
title: "Socket programming in C++"
date: 2010-06-09
forum: Programming Talk
---

### Post by iron_guitarist1987 on 2010-06-09
I am new to socket programming in C++, and have no clue on how to do it. I am trying to send ASCII commands through the Ethernet port to a motion controller using g++. It has an IP address burned to it, if this is of any help. Is there any easy way to do this?

---

### Post by Lucky. on 2010-06-09
I can't help you on here, but I do recommend [this book](http://www.amazon.com/TCP-Sockets-Second-Practical-Programmers/dp/0123745403/ref=dp_ob_title_bk) to help you out.  It's pretty cheap, and easy to follow.

---

### Post by DanielWaterworth on 2010-06-09
Does it have to be C++? If it does then I'd say use the [boost libraries]("http://www.boost.org/doc/libs/1_43_0/doc/html/boost_asio.html"). If it doesn't socket programming in python is a breeze.

Here's some simple code to get you started.

```
import socket

s = socket.socket(socket.AF_INET, SOCK_STREAM) # make a tcp socket
s.connect((HOST, PORT)) # make a connection
s.send('hello world') # send 'hello world'
print (s.recv(12)) # recv 12 bytes and print them
s.close() # close the socket
```There's also the twisted library for python that I've heard is pretty good.

---

### Post by tbastian on 2010-06-09
Here is a pretty good tutorial. Its in C, but If I'm correct, there is no native socket library for C++ (excepting boost). I would suggest working through their example line by line.

[http://www.linuxhowtos.org/C_C++/socket.htm](http://www.linuxhowtos.org/C_C++/socket.htm)

---

