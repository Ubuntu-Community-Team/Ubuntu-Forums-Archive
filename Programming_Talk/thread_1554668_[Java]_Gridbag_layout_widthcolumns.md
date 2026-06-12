---
title: "[Java] Gridbag layout width/columns"
date: 2010-08-17
forum: Programming Talk
---

### Post by SpinningAround on 2010-08-17
I'm started to work with Gridbaglayout but can't get more than four columns. If I try to add more than four items to one row will items only be added on top of each other. Is there a way to set or change number of columns?

---

### Post by PaulM1985 on 2010-08-17
If you are using GridBagLayout you should have a GridBagConstraints object with it.  The cell position where you add your component is given by the values gridx and gridy in your GridBagConstraints object.

This page describes GridBagLayout and has an example of how to use it:

[http://download.oracle.com/javase/1.5.0/docs/api/java/awt/GridBagLayout.html](http://download.oracle.com/javase/1.5.0/docs/api/java/awt/GridBagLayout.html)

Paul

---

### Post by lykeion on 2010-08-17
Couldn't help myself:

[http://madbean.com/anim/totallygridbag/](http://madbean.com/anim/totallygridbag/)

---

### Post by KdotJ on 2010-08-17
> **lykeion said:**
> Couldn't help myself:

[http://madbean.com/anim/totallygridbag/](http://madbean.com/anim/totallygridbag/)

lol nice. I can feel the frustration lol

---

