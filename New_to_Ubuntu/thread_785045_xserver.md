---
title: "xserver"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by shashwat0805 on 2008-05-07
can anybody tell me what is xserver ? when im trying to install nvidia geforce driver on my ubuntu it says " you are on xserver exit the server before installation" 
pls help!!!

---

### Post by mikewhatever on 2008-05-07
Try installing from recovery mode, usually second boot option. This way xserver never gets started.
[http://freedesktop.org/wiki/Software/Xserver](http://freedesktop.org/wiki/Software/Xserver)
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

---

### Post by PeterJS on 2008-05-07
X is the graphics subsystem that Linux uses, and the X Server is the program that handles drwaing the screen. To shut down X press, ctrl+alt+backspace, but X will automatically restart unless you tell it not to. To disable automatic restarts, in a terminal run:
```

sudo /etc/init.d/gdm stop

```

Once X is disabled, you'll want to restart it again when you're done, to get X to automatically restart again:
```

sudo /etc/init.d/gdm start

```

All of the above is the hard way to install the nvidia driver. If you want a tested stable driver the Hardware Driver manager at System > Administration > Hardware Drivers is much easier. If you want the newest drivers, install envyNG and have it install the drivers for you.

---

