---
title: "GLUT doesn't recognize 2 keys at once"
date: 2008-04-06
forum: Programming Talk
---

### Post by Arlanthir on 2008-04-06
Hi all,

I'm developing an Asteroids clone for college and I'm programming in windows and linux, with OpenGL and GLUT.
However, the exact same code functions properly in visual studio 2005 whereas the free-glut counterpart does not: When I hold UP and then press RIGHT it only sees UP.

Is there any way I can install another implementation of GLUT, or any common fix for this?

---

### Post by mike_g on 2008-04-06
I have never used glut, but are you sure you are scanning for keydown, and not keypressed. In the past I found that keypress polling generally gets the first key hit then flushes the input buffer. Maybe you need another event polling command?

---

### Post by Arlanthir on 2008-04-06
I'm using a library that notifies classes when a key is pressed and or released. I assume the code is not the problem, as it works fine in windows...

---

### Post by slavik on 2008-04-06
I would suggest not using GLUT for serious tasks as it was made to get a window with opengl open with least code possible and for some keyboard/mouse event handling.

I would suggest that you look at SDL as it provides more ways in which you can handle key presses and events.

---

### Post by Arlanthir on 2008-04-06
It's for college, I can't exactly choose :P
Thanks anyway ;)

---

### Post by slavik on 2008-04-06
is GLUT a requirement? you can use OpenGL with SDL ...

---

### Post by Arlanthir on 2008-04-06
Yes it is... Along with another lib they provide which I compiled in linux too =/

---

