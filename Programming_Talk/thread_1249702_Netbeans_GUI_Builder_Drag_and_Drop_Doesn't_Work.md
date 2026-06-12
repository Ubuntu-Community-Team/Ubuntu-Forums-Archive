---
title: "Netbeans GUI Builder Drag and Drop Doesn't Work"
date: 2009-08-25
forum: Programming Talk
---

### Post by MTGap on 2009-08-25
I've been trying to do just simple Java Swing apps and Netbeans is supposed to have a nice GUI Builder, but I can't seem to get it to work. It's basically supposed to work like Visual Basic where it is drag and drop. I'll drag one of the j components over and lines are supposed to come up for lining it up within the JFrame but nothing happens. And when I right click Add from Palette nothing happens. 

I've tried reinstalling it but it's the same and everything else seems fine. It's version 6.5 from the repositories what exactly could be wrong?

---

### Post by kpkeerthi on 2009-08-26
It depends on the Layout Managers you set for the container (and you need to set one always). Some layout managers let you drag and drop and allow you move the controls freely, and on some you need to 'place' the components and once placed they remain fixed until the Layout Manager's properties are modified (to make room and add more controls).

---

