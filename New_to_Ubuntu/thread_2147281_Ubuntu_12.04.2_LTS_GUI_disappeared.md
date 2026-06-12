---
title: "Ubuntu 12.04.2 LTS GUI disappeared"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by knightmt on 2013-05-21
Hi 
I have lost the Gnome GUI I think that is what has happened anyway,
 I am running ubuntu on a Samsung NC110, and only the terminal is coming up.
There may have been a conflict between the graphics driver and the automatic updates,
because I had been getting driver errors so removed the proprietry driver, then there
 was an update and I think I may have tried to reinstall it. Now I am writing this through my other pc.

I have been into the recovery mode I thought it allowed me to rewind the system,
 but now I cannot see that option and do not know what to do.
Sorry I have no idea what to do within the terminal or recovery mode.

Thanks Mat

---

### Post by dino99 on 2013-05-21
in recovery mode : activate the network, then select "dpkg" to try repairing, and finally select "continue" to boot.

questions:
- are you logged as Ubuntu ( aka unity) ? or something else ? (gnome-shell, gnome-fallback, ...)
- have installed external packages ? (ppa or else)

from a terminal, try to restore compiz/unity :
compiz --replace ccp &
setsid unity
(this should reload the icons)

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by Mariane on 2013-05-21
Try typing "startx" or "xinit" in the terminal.

---

### Post by knightmt on 2013-05-22
I am logged into Ubuntu though I have been getting messages about Unity 3D, something seriously wrong has happened now I cannot get into the recovery mode it is asking about root and boot sectors?
The reply from compiz --replace ccp & setsid unity
compiz(core) - Fatal: Couldn't open display
WARNING: no DISPLAY variable set, setting it to :)
Compiz (core) - Fatal: Couldn't open display :0
uity-panel-service: no process found
I think I have screwed something up I have not been able to shutdown so I have been holding the power button to power down.

---

### Post by Mariane on 2013-05-22
What happened when you turned it on again?

---

### Post by knightmt on 2013-05-23
It is now going straight into the recovery mode I am trying the network option but it seems to hang up after asking me whether I wish to remount the file system.
 I still do not really understand the recovery mode it seems to hang up mostly.
Okay I have rewound the system to a previous version.

---

