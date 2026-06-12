---
title: "Disable gdm startup, start console mode."
date: 2005-12-08
forum: Outdated Tutorials &amp; Tips
---

### Post by dartakaum on 2005-12-08
Hy, i would like to disable dgm and start in CLI, and when i do startx start fluxbox instead of gnome.

Now i'm starting gdm with fluxbox, how to disable it?

thanks,

---

### Post by blueworm on 2005-12-15
```
mv /etc/X11/Xsession /etc/X11/Xsession.old
```
That just makes a backup.
```
echo exec fluxbox > /etc/X11/Xsession
```
That will start fluxbox when you type startx.

---

