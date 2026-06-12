---
title: "single and double buffering in openGL??"
date: 2009-05-06
forum: Programming Talk
---

### Post by abhilashm86 on 2009-05-06
when we create a window and display or modify objects,
we initialize it to glut_single or glut_double, like how exactly do these get executed, procedure of control flow i din't understand??

---

### Post by Neheb on 2009-05-06
if I remember correctly:

with single buffer you write directly to the screen buffer and whatever is there when it's time to draw is what is drawn.

with double buffer you got two buffers, one that is drawn on the screen and one you are drawing to, and when you are finished drawing on buffer 2 you set that buffer 2 is the one that will be drawn to screen and you are drawing to buffer 1.

---

