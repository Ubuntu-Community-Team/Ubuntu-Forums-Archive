---
title: "g++ &amp; networking"
date: 2006-11-26
forum: Programming Talk
---

### Post by rvickers on 2006-11-26
I need to access ethernet ports via g++. So far all I've found is a document about ACE. Anyone point me in the right direction? Also, is there a good forum for g++?
Thx

---

### Post by Houman on 2006-11-26
Hi there;

You need to use BSD sockets , you can also use some other library to do it for you (like RakNet, or SDL_net) but using BSD sockets its probably best ;

Here are two tutorials I found:

[http://gnosis.cx/publish/programming/sockets.html](http://gnosis.cx/publish/programming/sockets.html)

[http://librenix.com/?inode=6491](http://librenix.com/?inode=6491)

You this helps;

Houman

---

### Post by rvickers on 2006-11-26
Thx
[http://gnosis.cx/publish/programming/sockets.html](http://gnosis.cx/publish/programming/sockets.html) fits the bill perfectly...
:D

---

