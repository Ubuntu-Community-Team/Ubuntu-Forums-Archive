---
title: "[SOLVED] Graphics and other functions for gcc"
date: 2007-07-19
forum: Programming Talk
---

### Post by dasan on 2007-07-19
Is there any way to get graphics and other functions like "int86" [in turbo c] in Gcc
:popcorn:

---

### Post by the_unforgiven on 2007-07-19
> **dasan said:**
> Is there any way to get graphics and other functions like "int86" [in turbo c] in Gcc
:popcorn:
Simple answer - no.
The way you have been using Turbo C is for MS-DOS which is a very primitive and legacy OS.
Modern operating systems don't let you access video resources directly, instead they have extensive APIs for graphics programming.

---

### Post by amo-ej1 on 2007-07-19
perhaps in a dos emulator ? like dosbox ;)

---

### Post by the_unforgiven on 2007-07-19
> **amo-ej1 said:**
> perhaps in a dos emulator ? like dosbox ;)
Is it really worth doing it?
I think, better option would be to use a cross-platform toolkit (GTK/QT) or graphics library like SDL or an even more generic language/API like OpenGL.
It's really worth spending time in learning these if you are serious about graphics programming.

---

### Post by dasan on 2008-01-07
Here is it
[http://arun.wordpress.com/2006/01/21/graphics-in-linux/](http://arun.wordpress.com/2006/01/21/graphics-in-linux/)

---

