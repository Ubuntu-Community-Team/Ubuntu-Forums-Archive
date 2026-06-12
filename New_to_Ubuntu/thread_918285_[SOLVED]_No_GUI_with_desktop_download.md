---
title: "[SOLVED] No GUI with desktop download"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by CAPTNCRIPT on 2008-09-12
I downloaded the desktop version of ubuntu from [www.ubuntu.com](www.ubuntu.com) I installed the iso with daemon tools unfortunately when I tried to load it i loaded into the terminal instead of the GUI ctrl + alt + F7 doesn't work i tried sudo applicable desktop - ubuntu and i've tried startx any ideas will be much appreciated.

---

### Post by dhtseany on 2008-09-12
Yo,
Does your network work? Can you ping google.com? If so try using apt to check and see if it's installed. If not try apt-get install gnome or kde and if those don't work search the repos' for the appropriate package(s).

Peace
Sean

---

### Post by jemate18 on 2008-09-12
on the terminal
type 
```
sudo apt-get install ubuntu-desktop
``` for GNOME

and
```
sudo apt-get install kubuntu-desktop
``` for KDE

---

### Post by CAPTNCRIPT on 2008-09-12
It states I already have the desktop downloaded how could I activate it through the terminal

---

### Post by LowSky on 2008-09-12
> **CAPTNCRIPT said:**
> I downloaded the desktop version of ubuntu from [www.ubuntu.com](www.ubuntu.com) I installed the iso with daemon tools unfortunately when I tried to load it i loaded into the terminal instead of the GUI ctrl + alt + F7 doesn't work i tried sudo applicable desktop - ubuntu and i've tried startx any ideas will be much appreciated.

> **CAPTNCRIPT said:**
> It states I already have the desktop downloaded how could I activate it through the terminal

You installed with daemon tools? You mounted the disc from Windows I'm presuming?
 Burn the .iso to CD and reinstall it the proper way,

---

### Post by adult swim on 2008-09-12
> **LowSky said:**
> You installed with daemon tools? You mounted the disc from Windows I'm presuming?
 Burn the .iso to CD and reinstall it the proper way,
+1
im not sure how it would even go about the partitions or installing when you are installing from a virtual drive within windows.

---

### Post by houbysoft.xf.cz on 2008-09-12
btw, have you tried
```

sudo gdm

```
or
```

sudo kdm

``` (for kubuntu) instead of startx?

---

