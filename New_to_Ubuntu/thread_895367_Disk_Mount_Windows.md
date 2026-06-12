---
title: "Disk Mount Windows"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-08-20
Hi Group,
How would I mount this disk?

/dev/sda1   *           1       18068   145131178+   7  HPFS/NTFS

I tried this:-

sudo /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

but it didn't work. It said:-  /dev/sda1: command not found


I've recently had to get a new computer after my last one died. I managed to get the old hard drive put into this machine where it resides as a second drive.....so I now have my new 250Gb hard drive on this machine....but it is partitioned so that I can run XP as well....all working.
I also have my old drive, also partitioned half Ubuntu and half XP.
Consequently, I have to mount three other drives.

I think I'll do them one at a time.

All the best,
Phil

---

### Post by ilexius on 2008-08-20
Hi groeswenphil,
the mount command is missing.
sudo **mount** -t ntfs ... should work!

Cheers,
Thomas

---

### Post by Paqman on 2008-08-20
If you want to dodge editting fstab by hand, just install [NTFS config](apt;ntfs-config), it'll mount your NTFS partitions no problem.

---

### Post by Melhisedek on 2008-08-20
Paqman you are my hero !

---

### Post by groeswenphil on 2008-08-20
just install NTFS config, it'll mount your NTFS partitions no problem

That worked.

Thanks,
Phil

---

