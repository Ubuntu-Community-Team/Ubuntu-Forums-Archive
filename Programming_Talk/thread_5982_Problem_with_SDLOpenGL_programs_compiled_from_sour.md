---
title: "Problem with SDL/OpenGL programs compiled from source"
date: 2004-11-23
forum: Programming Talk
---

### Post by norfenstein on 2004-11-23
I'm completely baffled by this: every program I compile that uses OpenGL for graphics and SDL for everything else works flawlessly except that I get no video output, only empty black windows. I get NO errors during the build process and everything else works fine (windowing, keyboard input, sound, etc.). Binaries of a program downloaded from somewhere else will work correctly but not when I compile from source. If glut is used instead of SDL then they'll work when I compile them. I've tried this with a number of different programs that I know should work and the result is always the same, does anyone have any idea what I could be doing wrong?

---

### Post by Roptaty on 2004-12-02
Strange thing indeed. 

I'm just guessing here:

You might not have the gl headers specific to your graphics card. For nvidia: sudo apt-get install nvidia-glx-dev

---

### Post by norfenstein on 2004-12-04
Wow, **thank you**, everything seems to be working now. I had no idea SDL required those. *Yay!*

---

