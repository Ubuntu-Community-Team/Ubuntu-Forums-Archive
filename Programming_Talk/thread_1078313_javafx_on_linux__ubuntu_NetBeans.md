---
title: "javafx on linux  ubuntu NetBeans ???"
date: 2009-02-23
forum: Programming Talk
---

### Post by hoboy on 2009-02-23
Does anybody knows if javafx is portable to linux yet ?
if so a link will be welcomed.

---

### Post by jespdj on 2009-02-23
There is no official JavaFX for Linux yet; the problem is that it takes time for Sun to make the included video and audio codecs work on Linux. They did promise that there will be JavaFX for Linux in the future.

I played with JavaFX this past weekend. Instructions to install the JavaFX SDK 1.0 [are here](http://www.weiqigao.com/blog/2008/12/04/using_javafx_1_0_on_linux.html) - but unfortunately this doesn't work anymore with the JavaFX SDK 1.1.

But scroll down to the bottom of that page; someone named Kaesar ALNIJRES posted a way to extract the JavaFX SDK 1.1 from the NetBeans plug-in. That's what I did, and it works (at least, I can use javafxc and the other tools from a terminal - didn't try if I can get it working through NetBeans).

JavaFX tutorials here: [http://www.javafx.com/learn/](http://www.javafx.com/learn/)
Also info here: [http://java.sun.com/javafx/](http://java.sun.com/javafx/)

---

