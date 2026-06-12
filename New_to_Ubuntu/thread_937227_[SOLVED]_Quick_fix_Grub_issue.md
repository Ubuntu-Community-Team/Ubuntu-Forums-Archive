---
title: "[SOLVED] Quick fix: Grub issue"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by pgar23 on 2008-10-03
ok so i just updated the kernel version from 7.10 to the newest 8.04 and the grub menu no longer is displaying my windows (yes i dual boot)..how can i put windows back on the grub list?? 
i checked the /boot/grub/menu.lst  and windows is no longer there..ubuntu ate it after update..lol

---

### Post by philinux on 2008-10-03
1. You may have a backup menu.lst with the exact erntry you need.

2. After other operating systems it would read like this.

title Windows1
rootnoverify (hd0,0)
makeactive
chainloader +1

where hd0,0 is the partition windows resides. First hard drive is hd0 and the first partition is 0. Grub counts from 0 upwards.

In Hardy this changes slightly to (sdx,x) as it labels all drives as sata even if they're IDE.

Post the output of 

```
sudo fdisk -l
```

---

### Post by pgar23 on 2008-10-03
> **philinux said:**
> 1. You may have a backup menu.lst with the exact erntry you need.

2. After other operating systems it would read like this.

title Windows1
rootnoverify (hd0,0)
makeactive
chainloader +1

where hd0,0 is the partition windows resides. First hard drive is hd0 and the first partition is 0. Grub counts from 0 upwards.

In Hardy this changes slightly to (sdx,x) as it labels all drives as sata even if they're IDE.

Thanks for the quick response philinux..how can i check the backups?? i just made another back up because i was commenting out the old kernels and then realized that windows was not there.

---

### Post by pgar23 on 2008-10-03
```

payton@thedesktop:~$sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5941    47721051    7  HPFS/NTFS
/dev/sda2            5942        6028      698827+  82  Linux swap / Solaris
/dev/sda3           11816       19457    61384365   83  Linux
/dev/sda4            6029       11815    46484077+   f  W95 Ext'd (LBA)
/dev/sda5            6029       11815    46484046    7  HPFS/NTFS

Partition table entries are not in disk order
```

---

### Post by philinux on 2008-10-03
Use
```
gksu nautilus 

```
and browse to /boot/grub/

have a look.

---

### Post by pgar23 on 2008-10-03
ok yup had a look, but i guess i didnt save a backup before this time..I have a backup form today before i started editing the list, but can u just tell me how to restore my windows on the grub menu from looking at the output of my posted fdisk -l?? Thanks for the help phil..

---

### Post by pgar23 on 2008-10-03
Duh! like I said quick fix..solved it myself.(I'm impatient lol)
(for my box)
```

title  Windows XP
root  (hd0,0)
makeactive
chainloader +1

```

---

