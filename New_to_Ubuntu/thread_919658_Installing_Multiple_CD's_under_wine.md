---
title: "Installing Multiple CD's under wine"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-09-14
I'm trying to install a game under the newest wine on Ubuntu 8.04.  I install the first cd fine.  I use:
```
wine eject
``` to eject the cd like I should(using umount is the wrong way to do it).  I insert the second cd.  It mounts fine under Ubuntu, but the setup running under wine won't detect it.  I don't remember the next step in the process.  I have used this method before.

---

### Post by mc4man on 2008-09-14
I use this instead, it maintains proper path for each cd, install is the same as in windows. (adjust red to match drive (in shown in winecfg) and install command (as seen on cd

```
wine [COLOR="Red"]D[/COLOR]:\[COLOR="Red"]setup.exe[/COLOR]
```

In other words after cd1 just push eject button **on the drive** and insert next cd, click ok in dialog box, ect.

---

