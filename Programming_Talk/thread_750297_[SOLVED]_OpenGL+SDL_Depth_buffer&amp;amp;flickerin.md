---
title: "[SOLVED] OpenGL+SDL Depth buffer&amp;amp;flickering"
date: 2008-04-09
forum: Programming Talk
---

### Post by paukku92 on 2008-04-09
I have a problem that may have something to do with the depth buffer. See, there is very disturbing "flickering" when you move on the scene. Also  I cant get the depthbuffer to work. depthbuffer setup is in the main.cc (in the package).

You may look at the program by running "rally".

Controls: 
F1=Fullscreen
esc=quit

Rotating:
q/a=x axis
w/s=y axis
e/d=z axis

Moving
UP=closer
DOWN=away from you

if you cant see the scene at start just press DOWN down for a little time.

EDIT: Solved, the near clipping plane was 0.0 i had to change it to 0.1 and it started working.

---

