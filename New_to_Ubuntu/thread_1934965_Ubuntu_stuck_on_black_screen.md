---
title: "Ubuntu stuck on black screen"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by gilatino on 2012-03-03
I cannot boot into ubuntu, it only shows a black screen. I installed nvidia driver and then had a problem about xconfig (*You do not appear to be using the NVIDIA X driver. Please edit your  X configuration file (just run `nvidia-xconfig` as root), and restart  the X server)*, so I searched the web and one recommendation was to uninstall the nauvea driver so I did and rebooted and now ubuntu stuck on this black screen.

---

### Post by forrestcupp on 2012-03-03
Do you have a command prompt at all? If so, or if you can get to one, you could try:
```
dpkg-reconfigure xserver-xorg
```And reset the xserver. Of course if you don't have root access, you'll have to put **sudo** in front of that.

---

### Post by kevdog on 2012-03-03
I believe pushing f1 on the blank screen should bring you back to a terminal prompt.  That should at least give you the ability to run commands in a terminal.

---

