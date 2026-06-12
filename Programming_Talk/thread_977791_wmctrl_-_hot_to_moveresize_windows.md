---
title: "wmctrl - hot to move/resize windows"
date: 2008-11-10
forum: Programming Talk
---

### Post by giuspen on 2008-11-10
is anybody good in using this software?
reading the instructions:
[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/)
i can do everything but what i'm really interested: move and resize a window.
i use commands like this, but without result:

wmctrl -r 'Software - File Browser' -e 0,300,300,300,300

maybe i use wrong syntax?

---

### Post by zhocchao on 2008-11-15
Hi
I've copy&pasted your line and it works for me. I only changed to german version. Maybe its File-Browser?

greetings

z

---

### Post by giuspen on 2009-02-07
Ok finally I have clear what was the problem: if the window is maximized, that action will not be visible since that command works on the unmaximized position/size of the window.

I would like to create an application to handle the tiling of the windows similar to the one available in windows xp, hope this powerful tool will help me to do this.
If anybody already implemented such application, please tell me.

---

### Post by giuspen on 2009-02-19
if anybody interested I finally created an application to handle the windows tiling.
you can try it [here]("http://open.vitaminap.it/en/windows_tiler.htm").
regards.

---

