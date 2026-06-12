---
title: "[SOLVED] Can I make a new partitions at a HDD in use"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by swotie on 2008-04-28
I have a /home drive at 400 GB ... Can I make a new partition at 300 GB, while the disk is used ... I don't want to loose some data

---

### Post by swotie on 2008-04-28
I would like to take 300 GB out of the 400 GB to a new partitons

---

### Post by swotie on 2008-04-28
I have a /home drive at 400 GB ... Can I make a new partition at 300 GB, while the disk is used ... I don't want to loose some data. I would like to take 300 GB out of the 400 GB to a new partitons

---

### Post by mlentink on 2008-04-28
No. You cannot repartition a mounted drive. You would first have to unmount it. 
I would recommend using the Live-CD, unmount all local drives/partitions and then use GParted to repartition.

---

### Post by NilsE on 2008-04-28
> **swotie said:**
> I have a /home drive at 400 GB ... Can I make a new partition at 300 GB, while the disk is used ... I don't want to loose some data. I would like to take 300 GB out of the 400 GB to a new partitonsSince it is your home drive you can not do it while it is active.  Boot with the live CD and then you can.  Any data in the way will just be moved to the front with no harm.

---

### Post by swotie on 2008-04-28
I have booted up at live-cd ... created a new partition in GParted ... but then I boot up in my normal system, I must manually mount it and I can't write to it ..

---

### Post by swotie on 2008-04-28
Disk /dev/sda: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026492

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123        2554    19535040   83  Linux
/dev/sda3            2555       22474   160007400   83  Linux
/dev/sda4           22475       60801   307861627+   5  Udvidet
/dev/sda5           22475       60801   307861596   83  Linux

Disk /dev/sdb: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f3ba0f6

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS



It is sda4 -  sda5 there is the problem

---

### Post by Metaljaz on 2008-04-29
Take a look at the below sites. 
I was booting Ubuntu Feisty and decided I wanted to try out pclinuxos 2007 and resized my partition using gparted and created another partition to install pclinux on without losing any data. I was then able to dual boot Ubuntu and PCLinuxOS 2007. When Hardy was released I decided to dump the other OS and installed just Ubuntu on the entire disk.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://www.linux.com/feature/53924](http://www.linux.com/feature/53924)
[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

Just a little help..

---

### Post by mlentink on 2008-05-01
Hmm. Don't really think so. If 'Udvidet' means "Extended" like I think it does, this is perfectly normal. You cannot have more than 4 primary partitions on a disk, but you can have as many extended ones as you like. I'm suspecting this is more of a permissions issue.

Could you post the content of your /etc/fstab file?

---

### Post by swotie on 2008-05-01
I have found a solution 

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=5b9bbbfc-ff4a-4ca6-ade6-d75aaacc7c10 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3
UUID=cefb275f-19c5-4834-aad2-b00deb0576a3 /home ext3 defaults 0 2
# /dev/sda1
UUID=ad80b6d0-0350-4c7d-83fd-9dbeec6c5248 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/sda4 /media/diverse ext3 defaults 0 2


This works

---

### Post by mlentink on 2008-05-01
> **swotie said:**
> I have found a solution 

...

This works

Yes, obviously you need to mount it somewhere...

Good to hear it works. Could you please mark your thread 'solved' so others won't unnecessarily come back? thx.

---

### Post by swotie on 2008-05-02
The "solved" function is gone from "tread tools" :-(

---

### Post by iSplicer on 2008-05-02
> **swotie said:**
> The "solved" function is gone from "tread tools" :-(

Its because of the forum upgrade, I am sure they will get that sorted out soon!

---

