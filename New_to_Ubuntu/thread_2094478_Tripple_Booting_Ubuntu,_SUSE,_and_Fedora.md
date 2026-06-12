---
title: "Tripple Booting Ubuntu, SUSE, and Fedora"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Ualuno on 2012-12-13
hello guys,
I installed OpenSUSE 12.2(1st) and Ubuntu 12.10(2nd). Ubuntu GRUB 2 boot loader controls the booting process. The aforementioned two OSes work great with each other. Now I really wanna to install Fedora 17 to configure a Tri boot System. Ubuntu 12.10 will be my primary OS and I use SUSE 12.2 and Fedora 17 for fun. 
Any tutorial on this? How can I do to add the third OS on the Bootloader to make sure all of them will work like a charm.
Thank you guys!!!!!!!!

---

### Post by monkeybrain2012 on 2012-12-13
Boot into a Ubuntu live usb, run gparted and create a partition for Fedora You may have to shrink Suse or Ubuntu, depending on how your hard drive is currently partitioned. So if Ubuntu is on the left most, followed by Suse you may want to shrink the Suse partition to the right to create free space for Fedora (You may want to make it an extended partition if in the future you want to add more oses)


Then shut down the computer and boot from a Fedora live usb and choose manually install into the free space you just created. Make sure you don't install boot loader (Fedora allows that option)

After installation is done (it is very fast comparing to Ubuntu installation), reboot (remove the Fedora live usb) into Ubuntu (which controls grub, correct?), mount the Fedora partition (say from the file manager) and in the terminal run

```
sudo update-grub
```

Then reboot and you will find Fedora in the boot screen.

Remember to do this (boot into Ubuntu, mount the Fedora partition and update grub) whenever you have a kernel update in Fedora.

---

### Post by debodas on 2012-12-14
As you already have two linux distros installed, I'll assume you know how to shrink partitions etc. (Do say if you want instructions on how to)

So, select 'custom install' when installing fedore (might be disguised as 'something else' instead of 'custom').

Anyway, reinstall grub while installing fedora (install grub on /dev/sda) and you should be away laughing.

---

