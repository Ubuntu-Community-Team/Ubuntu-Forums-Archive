---
title: "[SOLVED] Apache DocumentRoot on External Drive"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Korijn on 2008-05-21
Hey all, I've started getting into Ubuntu last week and so far I managed to transfer just about everything from my old Windows XP setup. I've got one last problem though. The DocumentRoot of Apache is the root of an External Hard Drive (connected through USB, NTFS). It's working if I log in, but it's not if I don't. So I reckon is booted on log-in, instead of on boot-up. How do I fix this? (I have zero knowledge of scripts except for PHP)

I currently got them to mount automatically through the NTFS Config Tool GUI.

Thanks a lot for the help!

---

### Post by Xiong Chiamiov on 2008-05-21
To change what's booted automatically, you'll need to edit your /etc/fstab.  If you post the results of
```

sudo fdisk -l

```
we can help you out.

EDIT: that's with the external mounted

---

### Post by Korijn on 2008-05-21
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b722b71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4592    36885208+   7  HPFS/NTFS
/dev/sda2            9668        9729      498015   82  Linux swap / Solaris
/dev/sda3            4593        9667    40764937+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885184 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1cf2686

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

```

---

### Post by Xiong Chiamiov on 2008-05-21
First, open your fstab for editing like so:
```

gksudo gedit /etc/fstab

```

Now we need somewhere to mount this to.  For this example, I'll put it in /media/external, mmk?
So then, we need to create the folder for it ahead of time:
```

sudo mkdir /media/external

```
If you want it somewhere else, just modify the path name in all my instructions.

From looking at what you posted, we can see that the 2nd drive is listed as sdb1.  So then, we'll add this line to the bottom of the fstab:
```

/dev/sdb1   /media/external   ntfs   defaults   0   0

```
Then mount all your drives with
```

sudo mount -a

```
and tell us how it goes.

---

### Post by Korijn on 2008-05-21
It worked like a charm! Thanks. :)

You can set this to solved now. ^^

---

