---
title: "compile a kernel and put it in different machine"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by abhisranjan on 2014-04-22
Hi all,
I need to compile a kernel which does just basic input output services (specifically copy from a flash,etc) ans load it into a new partition or a new computer and boot using that partition.
I compiled the kenel using "menuconfig " followed by make . make install and modules install,etc
I now have 4 files required for boot i.e. vmlinuz , config, system map and initrd.
I made a new partition(reiserfs) and made a new folder /boot.
I copied all the four file to /boot and ran "update grub" but grub would not recognise the new partition as bootable.
Could someone help me with what more is to be done.
I already tried LFS approach but its showing too many errors.

Thanks in advance.

---

