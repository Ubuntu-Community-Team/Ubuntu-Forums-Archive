---
title: "A simple question on compiling"
date: 2007-05-15
forum: Programming Talk
---

### Post by mahy on 2007-05-15
Hi y'all,

i'd like to compile and use Pidgin on my Feisty box, but i don't like the plain make install, and checkinstall 1.6.1 produces a faulty package. I wanna compile it in a 'portable' way, so that everything gets installed into a single directory, just like the official Firefox and Thunderbird releases (you just unpack it and run). Is it possible to achieve with ./configure and make parameters? If yes, how? TIA for any help.

---

### Post by FuturePast on 2007-05-15
$ ./configure --help
$ ./configure --prefix=/opt/pidgin

---

### Post by mahy on 2007-05-16
> **FuturePast said:**
> $ ./configure --help
$ ./configure --prefix=/opt/pidgin

THX a lot, i've gotta try it out? Is it really that simple? :-P

---

