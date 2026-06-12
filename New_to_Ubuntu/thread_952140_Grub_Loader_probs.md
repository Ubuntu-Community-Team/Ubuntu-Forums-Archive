---
title: "Grub Loader probs"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by will_s54 on 2008-10-18
Had bad memory and Grub Loader would go to memtest instead of Windows Vista . Replaced the memory and it retested ok.  The problem is now that on boot it still goes to memtest instead of Vista



Will
Ubuntu 8.04

---

### Post by stephanvaningen on 2008-10-18
You can look at your partition table to see which partition of which drive contains your Vista-installation, using (same as System -> Administration -> Partition Editor): 
```
 sudo gparted
```
Shows you partition information (you can also edit here: carefull!!). Don't edit anything, you don't need to. Safer would maybe be to list the partition tables with fdisk, so in gnome-terminal, type:
 ```
sudo fdisk -l
```
And look at the table. I.e:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6b2f3a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+   5  Extended
/dev/sda5           18749       19457     5695011   82  Linux swap / Solaris

```
In your example, you will find another list and one of the lines will mention NTFS. That is the partition you want to refer to in your grub-menu: /boot/grub/menu.lst
So now do:
 ```
sudo gedit /boot/grub/menu.lst
```
And look for the line mentioning Windows Vista.
Since this entry jumps to the memory-test, I can't tell you what to change there (I would assume some lines have gone missing there, but I can only judge that after having looked at your menu.lst-file if you would post it here), but you can add new lines in the same section somewhere, copy-pasting these lines:
```
 title        Windoze
 root        (xxxx,yyyy)
 savedefault
 makeactive
 chainloader    +1
```
==> Change xxxx with hd0 if it is located on the first hard disk in your computer, hd1 for the second, ...
==> Change yyyy with 0 if Vista is located in the first partition (so mentioned in /dev/sdq1 (where q is a for a fist hard disk, b for a second, ...)

Succes! and be **careful** when changing /boot/grub/menu.lst!

---

### Post by loseby on 2008-10-19
well here is my setup :




## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=bb271d85-4ef6-4025-aeec-f7d3cb681f2d ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=bb271d85-4ef6-4025-aeec-f7d3cb681f2d ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bb271d85-4ef6-4025-aeec-f7d3cb681f2d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bb271d85-4ef6-4025-aeec-f7d3cb681f2d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bb271d85-4ef6-4025-aeec-f7d3cb681f2d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bb271d85-4ef6-4025-aeec-f7d3cb681f2d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Dufangoer on 2008-10-19
Bump!                        thx   !   cheap wow power leveling --------------------------------**buy [eq2 plat](http://www.epaxx.com),  [eq2 gold](http://www.epaxx.com), [everquest platinum](http://www.epaxx.com), [rs gold](http://www.favgames.com/rs-gold/), [silkroad gold](http://www.favgames.com/silkroad-gold/),**

---

