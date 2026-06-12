---
title: "cannot boot ubuntu or windows"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by ELD on 2008-07-20
Here is fdisk:
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000730bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc4fcc4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4978    39985753+   7  HPFS/NTFS
/dev/sdb2   *        4979        5099      971932+  82  Linux swap / Solaris
/dev/sdb3            5100        9729    37190475   83  Linux


And my grub:
> 

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=360d4bd9-6895-48cf-a265-d778ae52d9b3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=360d4bd9-6895-48cf-a265-d778ae52d9b3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


I know all it is - is that grub is pointing to the wrong place, but i don't know a simple way to find out.

---

### Post by dexter.deepak on 2008-07-20
i never tried "map", but here is how i think it will work :
change the ubuntu root to
```
root (hd1,2)
```
and windows to 
```
root (hd0,0)
```
remove the map entries.

---

### Post by Elfy on 2008-07-20
It would appear to me that windows is on hd0,0, linux is on hd1,2

It looks also like the swap partition has a bootable flag?

It might also be worth checking what your groot line is set to - it looks like it's commented out with a #

---

### Post by ELD on 2008-07-20
Swap was set to boot wierdly, and ubuntu was actually on 0,2

Still can't figure where it's got windows though.

---

### Post by Elfy on 2008-07-20
Check you're device map in /boot/grub - I had one the other day where sda1 was hd1 and sda2 was hd0

Bit odd though linux is obviously not on hd0 :)

---

### Post by markbuntu on 2008-07-20
This can happen if your SATA drives are in the wrong plugs.

---

