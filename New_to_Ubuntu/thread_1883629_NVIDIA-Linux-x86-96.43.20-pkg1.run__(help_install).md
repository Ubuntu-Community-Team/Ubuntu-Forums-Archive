---
title: "NVIDIA-Linux-x86-96.43.20-pkg1.run  (help install)"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by jpba on 2011-11-19
Hello...

Can someone help me... how do i install this kind of file?

NVIDIA-Linux-x86-96.43.20-pkg1.run

Can some one tell me the commands to do it?
If possible put it here and i copy and paste.

Thanks

JP
Lisbon-Portugal

---

### Post by beew on 2011-11-19
Don't install the .run file. If you install the Nvidia driver manually you will have to reinstall it each time you upgrade your kernel. Just find "Additional Drivers", click on it and it will detect and install the driver for you. After you install, open a terminal and type
```
sudo nvidia-xconfig
``` and reboot, that's it.

---

### Post by jpba on 2011-11-19
> **beew said:**
> Don't install the .run file. If you install the Nvidia driver manually you will have to reinstall it each time you upgrade your kernel. Just find "Additional Drivers", click on it and it will detect and install the driver for you. After you install, open a terminal and type
```
sudo nvidia-xconfig
``` and reboot, that's it.


I receive this message, now what do i do?

jpba@Ubuntu-Wireless:~$ sudo nvidia-xconfig
[sudo] password for jpba: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

jpba@Ubuntu-Wireless:~$

---

### Post by beew on 2011-11-19
Don't worry about it,  basically it just says that it has to create a new xorg.conf file.  This is normal, just reboot and that's it.

---

### Post by lolpenguin on 2011-11-20
Try to NOT install the NVIDIA proprietary drivers you downloaded from its website (I broke my computer recently this way) but install them from Additional Drivers (jockey-gtk on gnome, jockey-qt on kde, jockey-text in console)
This is something I learnt from personal experience, but if you have to install them directly, you can.

---

### Post by jpba on 2011-11-21
> **lolpenguin said:**
> Try to NOT install the NVIDIA proprietary drivers you downloaded from its website (I broke my computer recently this way) but install them from Additional Drivers (jockey-gtk on gnome, jockey-qt on kde, jockey-text in console)
This is something I learnt from personal experience, but if you have to install them directly, you can.

OK... thanks, it works well now.

---

### Post by lolpenguin on 2011-11-22
> **jpba said:**
> OK... thanks, it works well now.

Good on you! When I tried it didn't work and I had to restore my computer. But really, the only real reason you have to install the drivers from the NVIDIA site is for a newer version with more features.

---

