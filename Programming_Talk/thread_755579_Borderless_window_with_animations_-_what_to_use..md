---
title: "Borderless window with animations - what to use."
date: 2008-04-15
forum: Programming Talk
---

### Post by escapee on 2008-04-15
I'm beginning work on a Multi-touch research project for my university and am currently working on coding some software for it while we wait for the funding and the materials to arrive for the display itself.  The first application one of my partners and I are writing is a virtual keyboard.

The keyboard will be mostly transparent, resizable by two inputs on opposing corner or any space that is not a key, and the keys will be animated to show when they are touched or held.  The keyboard will be invoked by a set hand gesture or when a text box is selected.

It is hosted on an Ubuntu 7.10 terminal currently, and we're not positive on which window manager we'll wind up using yet.  My question to you is what would you recommend I code this with as far as libraries/kits/frameworks/etc (we're using C/C++).  Thus far we've only really considered using X itself (recommended by our advisor) or using OpenGL, but we're not sure on what we're going with so I wanted to get some of your recommendations.  Any input is greatly appreciated.


Thanks guys!

---

### Post by escapee on 2008-04-15
Also just curious if anyone has used Python for things like this in any way?

---

### Post by kknd on 2008-04-15
use anything you want. You could use almost any programming language with GTK / Cairo.

---

