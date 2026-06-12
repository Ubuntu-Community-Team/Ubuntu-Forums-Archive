---
title: "OpenGL + freeglut: fgOpenWindow error message"
date: 2005-04-18
forum: Programming Talk
---

### Post by ct361 on 2005-04-18
Hi all!

After upgrading from warty to hoary I am trying to run a small glut-application I wrote. It does nothing except opening a window basically. I get

> freeglut_window.c:300: fgOpenWindow: Assertion `window->Window.VisualInfo != ((void *)0)' failed.


when I try to run it. Compiling works fine though. No warnings or errors.

From the freeglut mailinglist I discovered that this might have to do something with the X server and the default color depth. I tried 24 and 16bpp ... but it makes no difference. 

Is there a compatibility problem between some new X-Server-Version released with hoary and the freeglut implementation? Anyone got an idea what else causes this? With warty I had no trouble runing my app.

Thx.

PS: When I do not use glutInitDisplayMode(GLUT_DOUBLE) everything runs fine. Any known problems with double buffering and Xfree maybe?

---

### Post by mflash on 2005-04-22
I've been happily running freeglut for quite some time, both on Warty and Hoary
with no problems. Perhaps it's something related to your graphics card driver ?
What's your card ? 

Alternatively, post your source so people would have a chance to run it and see
what happens.

HTH,

Marcelo

---

