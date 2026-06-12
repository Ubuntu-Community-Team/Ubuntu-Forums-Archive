---
title: "WSOD on attempt to remove HPLIP"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-03
Hi, all;

I tried to remove HPLIP (the hewlett packard printer stuff) through adept, and now upon reboot, I'm getting a WSOD when KDE tries to start up.  Compiz starts, all my Autostart programs seem to be starting, but my screen is white before it flicks to black.  I tried removing the autostart for the systray, I tried reinstalling HPLIP, and I tried uninstalling it again.  Nothing's working, and I have no access to KDE.  I happen to have tilda installed, so I've got a terminal, and can start GUIs from it.  What should I do?

Intrepid, KDE 4.1.2

---

### Post by stephanvaningen on 2008-11-03
I think you should try to get more information out of the system concerning the problem.
What does
```
dmesg | tail
```
tell you right after startup?

---

