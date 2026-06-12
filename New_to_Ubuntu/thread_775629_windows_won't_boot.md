---
title: "windows won't boot"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ELD on 2008-04-30
Hi all when i installed ubuntu grubs menu said that ubuntu was it hda(1,0) when it was actually at 0,1 that took me ages to figure out.

But it won't boot windows either, how can i find where windows really is? :S

---

### Post by kesman on 2008-04-30
If you can boot to ubuntu, you can view your partitions with **fdisk -l** and figure out which one contains windows.

---

### Post by Bothered on 2008-04-30
Type the following in a terminal and post the result:

```
sudo fdisk -l
```

This will list the partition table(s) for your drive(s).

Also, post the result of:

```
cat /boot/grub/menu.lst
```

This will display the contents of your GRUB (bootloader) configuration.

---

### Post by ELD on 2008-04-30
fdisk output:
> 
liam@liam-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc4fcc4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4978    39985753+   7  HPFS/NTFS
/dev/sda2   *        5100        9729    37190475   83  Linux
/dev/sda3            4979        5099      971932+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000730bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS


windows grub bit:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd0,2)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Can anyone help me adjust it?

---

### Post by Paqman on 2008-04-30
You've got two NTFS partitions there. One on each drive. i'm guessing that Windows is on the first drive, and that your other one is data?
If so:
```

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```
Should sort you out. If it's the other drive then substitute
```

root (hd1,0)

```
You'll need to edit these files using sudo, btw.

---

