---
title: "Won't mount partition on startup"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2011-09-26
I've always had the last command in my fstab file to mount a windows partition during bootup.  Now it stops during the boot process and says it can't.  I skip it and then mount manually (sudo mount -a) after the boot process and it works.

Anybody else seeing this?

---

### Post by FerroPower on 2011-09-26
its working, maybe you need to recheck your configuration fstab file.
I load my partition with following command in fstab. (it gives my user a/c exclusive read/write access)


[COLOR="Blue"]/dev/sda2         /media/sda2       ntfs       auto,umask=0022,uid=1000,gid=1000  0  0  
[/COLOR]

---

### Post by seattle vic on 2011-09-26
Yes, that did it.  Must have been the uid and gid settings which I did not put in, thanks.

---

### Post by mziel on 2011-09-29
The problem is in installer (I think).

After installing beta2 64-bit on clean disk, it gave 1 to fs_passno (sixth field in fstab) for created ntfs partitions. While booting fsck tries to... fsck ;) that partition.
Changing 1 to 0 helps.

So it's not uid/gid thing.

---

