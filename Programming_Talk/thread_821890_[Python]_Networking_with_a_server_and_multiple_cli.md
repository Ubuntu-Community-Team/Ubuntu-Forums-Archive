---
title: "[Python] Networking with a server and multiple clients"
date: 2008-06-07
forum: Programming Talk
---

### Post by durand on 2008-06-07
I'm really not sure how I would go about doing networking efficiently in Python. Are there any good tutorials that people recommend? I've read tutorials about echo server/clients with sockets and so far, thats what I've been using for my program.

I guess I don't have a programmer mind set because I'm finding it really difficult to put together a system for multiple users.

To put this into context, this is for a card game called Big Two. Basically, I need a server to manage a maximum of 4 clients and since it is turn based, there should be some way of communicating with each client separately. I'm not really sure how to do this in python.


Thanks in advance.

---

### Post by red_Marvin on 2008-06-07
If you want to write it all by yourself I would recommend [Beej's guide to network programming]("http://www.beej.us/guide/bgnet/"). It's for c, but the functions provided for python are similar, just *import socket* and then *help(socket)* and check the differences.

If you want something more of a ready made framework, there are the *twisted* modules, but I don't know much about them.

---

### Post by pmasiar on 2008-06-07
Not sure what is your current level skill. Networked app is 100 times more complicated than plain desktop: you need to deal with client AND server AND connection AND asynchronous communication.

twisted is (one of many) framework to create such apps. Docs are less than perfect, but there are always users and devels mailing lists :-) where you can ask questions

---

### Post by durand on 2008-06-08
Well, I am pretty new to python but networking is essential to this project so I need to understand it sooner rather than later. I've been delaying looking at twisted due to the fact that many seem to think it is a hard module to learn but I guess its my best chance.

That book may be useful if I wanted to learn raw networking techniques but I've been playing with sockets and they just feel a bit too low level for this so I think I'll learn twisted. Thanks for your input!

---

### Post by durand on 2008-06-08
Oops, I meant guide, not book.

---

