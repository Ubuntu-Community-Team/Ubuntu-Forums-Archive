---
title: "C++ sockets"
date: 2011-07-07
forum: Programming Talk
---

### Post by gmargo on 2011-07-07
client / server example code in Python, Perl, C, Java:

[http://www.prasannatech.net/2008/07/socket-programming-tutorial.html](http://www.prasannatech.net/2008/07/socket-programming-tutorial.html)

---

### Post by nvteighen on 2011-07-08
> **ProGestapo said:**
> Does anybody know of any good C++ socket libraries? Or any GOOD tutorials? All I need is basic send/receive and connect. I'm trying to create a simple client to connect to a server.

Thanks in advance.

I think people tend to use the C BSD Socket library and wrap a C++ OOP layer around it (or maybe not even that). It is quite unlikely that people write an alternative to it, given its quality and widespread usage in UNIX/-like OSs.

IMO, this is the best tutorial: [http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/). It's for C, but you can follow it if you know C++... and after that wrap things into classes, as usual.

Nevertheless, maybe there is a C++ binding for this already implented, but I don't know.

---

