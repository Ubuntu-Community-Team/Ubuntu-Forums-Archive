---
title: "My Ubuntu USB stick mounts as read only"
date: 2019-02-09
forum: New to Ubuntu
---

### Post by t5404tmz on 2019-02-09
I created a bootable USB drive and it works fine, but I want to utilize some of the free space on it.

How do I mount it as read/write?


Partition Type:  Hidden HPFS/NTFS (Bootable)

Device:  /dev/sdb1

output from mount command:
/dev/sdb1 on /media/master/Ubuntu-MATE 18.04.1 LTS i386 type iso9660 (ro,nosuid,nodev,relatime,nojoliet,check=s,map=n,blocksize=2048,uid=1000,gid=1000,dmode=500,fmode=400,uhelper=udisks2)

---

### Post by CatKiller on 2019-02-09
> **t5404tmz said:**
> How do I mount it as read/write?

You can't. The install image is read-only by design.

You can, however, add persistence to it.

---

### Post by t5404tmz on 2019-02-09
Sorry...

I just had to create a new partition.

Mental error!  Not the first, won't be the last.

Thanks for the help!

---

