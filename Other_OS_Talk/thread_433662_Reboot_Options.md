---
title: "Reboot Options"
date: 2007-05-05
forum: Other OS Talk
---

### Post by SnowLinux on 2007-05-05
I'm finding my way around the Edubuntu 7.04 release and with KDE installed,
I want to know how I get an option to reboot automatically to Windows as I have dual boot PC!


By the way, it is a damn good idea to develop a PC system geared up with education software for youngsters.

---

### Post by meborc on 2007-05-05
you can edit the menu.list file under /boot/grub

there is a the place you can choose what is the default OS to boot into... change the number 0 (the first line in grub menu) into the number of the line your windows is in the grub...

be sure to make backup of the file first as when you mess up, it would be easier to recover :)

---

### Post by SnowLinux on 2007-05-05
I appreciate what your saying about making Windows default bootup
but what I actually meant was when you come to shutdown Edubuntu having a
menu option to reboot to Windows automatically on only the next boot while keeping
the default boot on Edubuntu.

This is an option available with PCLinux which I use on another dual booting PC

---

