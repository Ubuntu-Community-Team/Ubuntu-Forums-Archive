---
title: "X Window geometry"
date: 2009-11-18
forum: Programming Talk
---

### Post by pokerbirch on 2009-11-18
I'm working on a simple Python script that will rearrange some window positions on my Ubuntu Gnome desktop. I have a function that shells the xwininfo command to get the geometry of a given window, however i cannot seem to find a similar function capable of moving the window position.

I am currently using xdotool's movewindow() function and have also considered wmctrl and python-xlib but these mean i have a dependency on a large library, of which i am only using one function.

Is there a default X or Gnome command capable of setting a window position? If not, can i somehow call the XSetGeometry() function without requiring the python-xlib library?

TYIA.

---

### Post by StephenG on 2009-12-18
This is my one real complaint with all the Ubuntu installs I've done -- that every time I open a window it's in the far upper left corner, not where I had previously positioned it.  Whenever you get this figured out, please post it.  Thanks.

---

