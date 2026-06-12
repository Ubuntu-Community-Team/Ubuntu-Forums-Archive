---
title: "OpenGL Mouse Functions"
date: 2008-03-18
forum: Programming Talk
---

### Post by justgrant2009 on 2008-03-18
I'm taking a class learning about 3d Animation and programming with openGL.  We created a model of a lamp for our first assignment and have since used it in each new project, just adding new functions to it.  I have programmed the ability to push a key on the keyboard and have the lamp rotate around an axis I've chosen.  But now, i need to be able to press the left mouse button anywhere in the window and have the lamp rotate until the button is released.  I've tried setting up a while loop that says while the state is GLUT_DOWN, rotate, but when i click, nothing changes, and the program actually locks up on me.  If anyone can help with this it'd be very much appreciated.

---

### Post by ha1f on 2008-03-18
Well, im not sure how you're doing the keyboard rotation (should really be just as simple), but what you could do is (once every event loop) if the mouse state is detected as GLUT_DOWN, rotate (don't fall into a loop).  Though, I wouldn't be suprised if you just aren't polling events in the loop you made that is locking up.

---

