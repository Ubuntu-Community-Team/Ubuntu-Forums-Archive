---
title: "Satellite Video x3100 (GMA965)"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by frogzombie on 2008-05-21
I am having a world of issues with 8.04. After searching the forums, the other X3100 thread had me install a few packages that were already installed, but my xorg.conf is still using:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

and i cannot run any games with that setting. However, all additional eye candy and compiz will run, as well as an snes emulator. Any 3d games will not run and keep asking for an openGL compatible device. If i change the xorg.conf to reflect the intel chipset, it breaks xserver and causes me to run in 800X600. dpkg reconfigure fixes this quickly though. 

The dpkg does not allow for any setting changes, it just sets it back to defaults with this output:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080521170630


I am at a loss after about 8 hours of troubleshooting.

Please help.

---

### Post by shifty_powers on 2008-05-21
ultmiatley, i'm afraid that the x3100 is a big pain in the ***.

the driver for it is blacklisted in the kernel.

read

[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

and will give you an option ;)

---

### Post by frogzombie on 2008-05-21
"8.04 does not blacklist i965 cards."

From that site it states that my card is not blacklisted, and I do _NOT_ have issues running compiz. Only OpenGL required games.

---

### Post by frogzombie on 2008-05-21
bump?

---

### Post by frogzombie on 2008-05-22
anyone?

---

### Post by shifty_powers on 2008-05-22
out of interest, what is the output of:

```
lspci
```

---

