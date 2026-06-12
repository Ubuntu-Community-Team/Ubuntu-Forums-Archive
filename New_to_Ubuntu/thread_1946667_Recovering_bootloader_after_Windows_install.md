---
title: "Recovering bootloader after Windows install"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by JamButty on 2012-03-25
Just wiped and reinstalled my Windoze partition and need to get the bootmenu back to get back to the sane side of the machine.
I know there is a good tutorial out there about how to do this with the livedisk, but I am not finding it
Thanks.

---

### Post by kdane4 on 2012-03-25
hi,

try yannbuntu's awesome boot repair tool

ubuntuforums.org/showthread.php?t=1769482

---

### Post by garvinrick4 on 2012-03-25
In live cd:
Open Terminal:
```
sudo mount /dev/sda5 /mnt
```
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```

I am using sda5 as example use your own partition you want to control grub.

```
sudo fdisk -l
``` (lower case L) to find linux install if do not know its sda#

---

