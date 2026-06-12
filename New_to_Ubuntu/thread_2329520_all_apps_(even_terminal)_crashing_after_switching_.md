---
title: "all apps (even terminal) crashing after switching window manager"
date: 2016-07-02
forum: New to Ubuntu
---

### Post by zephyr2 on 2016-07-02
I'm running Ubuntu MATE 15.10 on a 2011 System76 Gazelle Pro laptop. 

After changing the window manager from Marco to Compiz*, every app I try to run crashes within seconds, even after a reboot. The text editor (Pluma), the Find Tool, even terminal and the file manager (Caja).  The error report that comes up (generated, I think, by Apport) indicates the same Xsession error for each crash:


```
(yelp:1833): Gdk-WARNING **: /build/gtk+3.0-plzeMy/gtk+3.0-3.16.7/./gdk/x11/gdkwindow-x11.c:5540 drawable is not a native X11 window
```


Note: the system *itself* doesn't appear to be crashing--I'm not, for instance, being sent back to the login screen, the mouse isn't freezing, etc. But since I cannot run Terminal, I cannot look for error messages, and as I said the behavior persists after a reboot. Anything else I can try? :( 


[SIZE=1]
* Just for background: my system was behaving OK today as I tested a live usb of 16.04, then shut down and booted into 15.10 again. 

While in 15.10, everything seemed fine until I changed the  window manager from Marco to Compiz.  (I did this b/c Marco has this  annoying bug: whenever I grab and drag a window, it won't move the first time and generates an error report.  I read elsewhere that Compiz doesn't have this problem.) In Compiz, however, all my windows lost their  borders (no close / min / max buttons), so I switched back to Marco, only to be unable to launch anything without crashing![/SIZE]

---

### Post by Omar_Jair on 2016-07-02
You probably damaged the system and you might have to do a full reinstall, another thing you can do is press [ctrl+alt+f1] to open the terminal session without a desktop and reinstall Marco.

---

### Post by QDR06VV9 on 2016-07-02
If you can get a working terminal you can replace compiz with
```
marco --replace
```

---

