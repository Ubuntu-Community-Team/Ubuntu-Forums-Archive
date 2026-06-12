---
title: "Freely Distributing Widgets"
date: 2009-12-24
forum: Programming Talk
---

### Post by Majorix on 2009-12-24
I am trying to build cross-platform software with a GUI, using Python.

So far I have looked at Glade and wxGlade. To my frustration, they worked with "containers". I would have to say this is a very bad approach to building GUI's.

I like the idea of Java on NetBeans; where you can drag, drop wherever you want, resize, and so on.

Is there perhaps a setting/preference I am missing, or is there no way to build GUI's with Python the way I want to?

---

### Post by Majorix on 2009-12-25
*bump*

---

### Post by Zugzwang on 2009-12-25
Actually, what is so bad about using containers for building GUIs? In Java, I found myself only using the GridBagLayout and ignoring this Netbeans drag&drop-stuff as these containers make sure that the windows designed are resizeable very well whereas the drag&drop stuff seems to be a little bit non-deterministic.

---

### Post by nvteighen on 2009-12-25
First... there no such thing as a "Glade GUI". Glade is a way to use GTK+.

GTK+ prefers containers because it's much easier to deal with them than using a grid. You have to realize that GTK+ was designed to aid programmers writing their GUIs in C in a text editor... IDEs are just an afterthought and an accident (in aristotelian sense :P).

---

