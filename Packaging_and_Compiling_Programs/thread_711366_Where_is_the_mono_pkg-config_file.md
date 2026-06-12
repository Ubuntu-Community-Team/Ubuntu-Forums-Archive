---
title: "Where is the mono pkg-config file?"
date: 2008-02-29
forum: Packaging and Compiling Programs
---

### Post by jsoderba on 2008-02-29
I'm trying to compile muine ([http://muine-player.org/wiki/Main_Page](http://muine-player.org/wiki/Main_Page)) from SVN because the one in universe keeps crashing, but the configure script complains it can't find the mono package. Indeed, "pkg-config --libs mono" can't find it. I've installed the mono-devel package, which did not contain mono.pc, so I'm wondering if it is in an other package or it has been renamed (muine hasn't seen much development lately).

---

### Post by jsoderba on 2008-02-29
Never mind, I found out my problem. I did an apt-get build-dep muine and it installed libmono-dev, which contained the file. I hastily assumed that libmono-dev would be included in mono-devel. 

Oh well.

---

