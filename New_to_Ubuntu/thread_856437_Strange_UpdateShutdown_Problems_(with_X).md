---
title: "Strange Update/Shutdown Problems (with X?)"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by vertexoflife on 2008-07-11
Hello. I'm running a gateway GT5048 with an ATI Radeon x1600, with GNOME and KDE installed. I use kdm as default with compiz as a window manager.

Whenever I Update via GUI, my screen will go entirely black and then stop working entirely. (Restarting X with Crtl+Alt+Blackspace does nothing or alt+crtl+f1 to get to terminal does not either.)

I get something similar when I try to shutdown or restart via GUI. The programs will shut down, and my screen will go black like it is about to shut down, but it wont, it will just sit at a black screen doing nothing until I hold the power button for awile. THEN the kubuntu logo with the progress par will display then shut down completely.

---

### Post by dracayr on 2008-07-11
I have a similar problem. didn't find a solution yet. Once I tried adding the line

Option "XaaNoOffscreenPixmaps"

to my xorg.conf. that helped, but then other, worse problems occured. maybe it will work for you...

dracayr

---

### Post by vertexoflife on 2008-07-11
I'm trying to figure out if this is a bug in the OS or if it is just something in particular with my setup.

---

### Post by dracayr on 2008-07-11
it probably is something particular in your hardware combined with X

dracayr

---

### Post by vertexoflife on 2008-07-11
bump

---

