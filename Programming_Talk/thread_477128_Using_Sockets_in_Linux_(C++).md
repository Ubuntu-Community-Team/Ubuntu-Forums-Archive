---
title: "Using Sockets in Linux (C++)"
date: 2007-06-18
forum: Programming Talk
---

### Post by xMemphisx on 2007-06-18
Alright, so i'm learning to use winsock with C++, and i want to try and use it to write a simple cross-platform chat for both windows and linux systems. i'm not sure though, how to use winsock with Linux, in windows, i just included the windows header (windows.h), but is there a linux alternative? or a single header file alternative that will work with both systems? 

I know this is kind of a newb question when it comes to this... but i haven't been able to find a good answer so i thought i'd ask. Everything i've seen just says to include windows.h, but is there a winsock header file or something similar to it that both platforms are capable of?



[Edit]
Nevermind. I'm a total idiot.

---

### Post by PandaGoat on 2007-06-18
[http://beej.us/guide/bgnet/output/html/multipage/index.html]("http://beej.us/guide/bgnet/output/html/multipage/index.html")  is a good tutorial.  The headers are sys/sockets.h and a few others.  It's all in the tutorial.

---

