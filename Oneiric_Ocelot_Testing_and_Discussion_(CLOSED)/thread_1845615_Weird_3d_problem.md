---
title: "Weird 3d problem"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2011-09-17
I use nvidia-current, 64-bit, on gforce 9400m g.

Regular ubuntu 3d apps work fine (gnome-shell, glxgears, google earth, etc.). Direct rendering is enabled. However, several external 3d apps stopped working lately, and they give me weird messages upon launch:

Lugaru says: 
```
SDL_SetVideoMode() failed: Couldn't find matching GLX visual
forcing 640x480...
```

Atom Zombie Smasher says:
```
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  8 (X_MapWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  32
  Current serial number in output stream:  34
```

Diablo via Wine says:
```
No useful pixelformat found! Please check your graphiccard driver.
```

I tried moving to xorg-edgers, and X just stopped loading altogether. I ppa-purged it and tried nvidia 173 drivers, and this did not help.

Any idea what could be the problem?

---

### Post by Sworddragon on 2011-09-17
Maybe it is related to these problems:

[http://ubuntuforums.org/showthread.php?t=1845489](http://ubuntuforums.org/showthread.php?t=1845489)
[http://ubuntuforums.org/showthread.php?t=1845612](http://ubuntuforums.org/showthread.php?t=1845612)

---

### Post by Wise Ferret on 2011-09-17
> **Sworddragon said:**
> Maybe it is related to these problems:

[http://ubuntuforums.org/showthread.php?t=1845489](http://ubuntuforums.org/showthread.php?t=1845489)
[http://ubuntuforums.org/showthread.php?t=1845612](http://ubuntuforums.org/showthread.php?t=1845612)

Thank you. This Wine problem seems to be related to the issue with diablo, but not to the problems with lugaru and AZS.

I wish I knew what to look for in order to diagnose this...

---

