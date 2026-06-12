---
title: "how check X settings"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by akkad on 2008-05-29
i would like to know if am running 24 bit color mode on X, so what is the command??

---

### Post by sayakb on 2008-05-29
Open a terminal and type:
```
xwininfo
```
And click on any window. TrueColor should indicate highest color depth selected.

---

### Post by Maestro23 on 2008-05-29
I know you can check your xorg.conf for default depth.

> cat /etc/X11/xorg.conf | grep Defaultdepth

or 

> xwininfo

---

