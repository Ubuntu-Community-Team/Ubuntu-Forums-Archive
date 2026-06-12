---
title: "Virt Box icon"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by benjie1 on 2012-03-30
Installed Virtual Box OK, v 4.1.10. Runs fine but the desktop icon is plain (generic) and when I click it, says it is not trusted. Can't get the real icon and have to open it in terminal. Can you help with this. Have Ubuntu 11.10, and gnome.   Tks.      Bob

---

### Post by jerome1232 on 2012-03-30
How did you install it?

Use a .deb from here [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

This will give you a regular icon that you can drag out to your launcher.

---

### Post by benjie1 on 2012-03-31
Installed it from Oracle. Will install from your link and hope it gives the icon. Was hoping not to have to re-install, but no prob. Thanks      Bob

Just installed it. There is an icon in the dash home bar but dragging it to the desktop gives the same  not trusted icon as I started with.       Bob

---

### Post by jerome1232 on 2012-03-31
Why put it on your desktop, put it on your launcher, that what it is for, launching things.

---

### Post by benjie1 on 2012-04-01
Have lot of icons on desktop where I like them. Can it be done? Don't care for the launcher.

---

### Post by jerome1232 on 2012-04-01
Assuming it's still done with .desktop files, you should be able to open it with a text editor and manually set the image path.

```
gedit /path/to/Desktop/Virtualbox.desktop
```

The icon is probably in /usr/share somewhere, look for /usr/share/virtualbox would be my guess.

---

### Post by benjie1 on 2012-04-02
Thanks. Found the icon in /usr/share/applications  Seems it should work now.  I'll mark it as solved.

---

