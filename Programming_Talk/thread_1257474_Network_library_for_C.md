---
title: "Network library for C"
date: 2009-09-03
forum: Programming Talk
---

### Post by FrankBro on 2009-09-03
I've started programming with c again lately and was wondering if you guys knew a good library easy to learn to do network stuff (access online database, work with php, etc.) . 
I've recently learned GTK+ and loved their online tutorials step by step and wish i could find something similar for network stuff.

Any suggestions ?

Thank you.

---

### Post by phrostbyte on 2009-09-03
Raw BSD sockets is the low level networking interface. [http://mixter.void.ru/rawip.html](http://mixter.void.ru/rawip.html)

If you want to make web apps look into CGI. That's as easy as using printf to output raw HTML.

If you want to work higher level then that you're probably going to have to link to some libraries. Glib may have some higher level networking routines, like improved support for hostnames. :)

---

