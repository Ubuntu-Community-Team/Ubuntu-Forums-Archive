---
title: "resolution changes"
date: 2013-04-30
forum: Programming Talk
---

### Post by thedardanius on 2013-04-30
I see most opengl games change resolution to go into fullscreen mode. Why is this? cant you just maximize your application and you have a window over your entire screen?
Is changing resolution good for performance???

---

### Post by ofnuts on 2013-04-30
At lower resoluitons you need less CPU/GPU to produce the image. And going fullscreen allows the game to cover the full screen at a lower resolution than the other apps require, and lets it short-circuit some of the graphics software layers...

---

### Post by thedardanius on 2013-04-30
so my app simply resizes the window until it covers the entire screen, with default resolution. Is this a bad practice?

---

### Post by ofnuts on 2013-04-30
Games are very specific apps with very specific needs... What is bad practice for the other apps is the inability to work in a standard window...

---

