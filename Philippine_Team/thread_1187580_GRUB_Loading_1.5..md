---
title: "GRUB Loading 1.5."
date: 2009-06-14
forum: Philippine Team
---

### Post by zilu54 on 2009-06-14
[http://ubuntuforums.org/showpost.php?p=7452224&postcount=97](http://ubuntuforums.org/showpost.php?p=7452224&postcount=97)

maganda gawan ku nga tu ng bagung thread.

---

### Post by loell on 2009-06-14
post your grub menu.lst

---

### Post by zilu54 on 2009-06-14
hindi ko pa ma post ang grub menu.lst kasi hindi man lang nag oopen ang ubuntu?
nanun lang siya "GRUB Loading 1.5."

---

### Post by loell on 2009-06-14
do you have a livecd? if so, use it to boot the laptop.

---

### Post by zilu54 on 2009-06-14
> **loell said:**
> do you have a livecd? if so, use it to boot the laptop.
```
# sample /boot/grub/menu.lst entry for memtest86
#
# This example assumes the contents of /boot is on the root partition.
# If your /boot is on its own partition, remove /boot from the 'kernel' line.

title  memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin

title  memtest86+ (serial console 115200)
root   (hd0,0)
kernel /boot/memtest86+.bin console=ttyS0,115200n8
```
hayan po, sana tama tung nahanap ku.

---

