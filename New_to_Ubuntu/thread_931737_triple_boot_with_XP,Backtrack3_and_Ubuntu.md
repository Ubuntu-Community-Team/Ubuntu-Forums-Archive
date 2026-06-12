---
title: "triple boot with XP,Backtrack3 and Ubuntu"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by bren1104 on 2008-09-27
Hello everyone i have been trying to make this work for hours now and am having no luck. I have tried editing my grub file but to no avail. When i try to select Backtrack 3 to boot from my computer just reboots and no error message or nothing. Could someone help me with this. Here is the output of my grub config file:



## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=cb976062-f773-415b-85bd-f7ccb8fab69a ro quiet splash xforcevesa
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=cb976062-f773-415b-85bd-f7ccb8fab69a ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
chainloader +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title Backtrack3 (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda2 ro vga = 791
savedefault
boot

---

### Post by Presto123 on 2008-09-28
Download SuperGrub and burn to a disk. Take that and try to configure your Grub file. It's been a while since I've used it, but after a bit, it's pretty simple to use and SHOULD get you somewhere usable.

SuperGrub is pretty good at grabbing the missing partition. If you need help from me with it, I will have to look back over the menus/etc.

---

