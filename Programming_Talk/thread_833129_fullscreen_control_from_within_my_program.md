---
title: "fullscreen control from within my program"
date: 2008-06-18
forum: Programming Talk
---

### Post by Clive McCarthy on 2008-06-18
My next system issue is to figure out how to invoke fullscreen mode from _within_ my program?

I found advice about manually doing what I want by using:
system>preferences>keyboard short cuts>window management>toggle fullscreen mode
Which does what I need. :)

I need to unleash my OpenGL/glut program from the fenestration's mullions. A system call to the window manager is probably what I need...

---

### Post by 23meg on 2008-06-19
Moved to Programming Talk.

---

### Post by escapee on 2008-06-19
Just call the view in FULLSCREEN using GLUT I believe if it's just OpenGL/GLUT.

---

### Post by Clive McCarthy on 2008-06-19
One of the problems encountered with Ubuntu/Gnome/glut is that glutFullScreen() does not got to full screen and neither does glutEnterGameMode().

The solution I found, from another posting exchange I had, is to install & use wmctrl -- which does what is needed.

---

### Post by escapee on 2008-06-19
Hmm.  Didn't know that one.  Good call.  I just assumed it worked properly as SDL has for me in the past.

---

