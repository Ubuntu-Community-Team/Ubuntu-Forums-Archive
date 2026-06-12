---
title: "Formatting Hard drives"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by loseby on 2013-05-23
My system is dual boot and I have a hard drive ( scsi3 ) that I dont want windows to keep bringing up messages about. I want to delete all partions and create new ones using the linux system., at the moment it show as msdos filesystem. I have looked and cant find anything........ is there a good program or something like the computee managent  hard drives that windows has ?

edit: just went into windows and deleted the partions but cant find it now on Ubuntu

edit: found gpart and used that, still whats the best system to use on a 500gb drive

---

### Post by verbin on 2013-05-23
To see what disks are found by fdisk use:
```
# fdisk -l
```
Something similar to disk manager from windows is "gparted" but the true advanced formatting and partitioning is done by command line, you just have to know what you're doing.

I think gentoo or archlinux webistes have a good guide.

---

### Post by loseby on 2013-05-23
Well managed to get it partioned and formatted but I dont have permision to use it

its shows us /dev/sdd1 and has a pic of a key ...  now before I started playing around with it I had the drive encrypted

edit: I have only being using ubuntu for banking etc and have basically forgotten the small amount I knew. Found the disk tool I needed , lot easier and better then  that other shat.  Anyway have removed that hard drive and put another one in and am now working on that. Everything seems ok and am copying files back from windows .... the other drive is not a windows drive in another PC

Will encrypt it after this and hopefully everything will be find

Just one final question, if you encrypt this drive can you view it in another Ubuntu machine ?

---

