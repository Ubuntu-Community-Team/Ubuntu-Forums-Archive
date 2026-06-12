---
title: "[SOLVED] Mounting and all that..."
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Qtips on 2008-09-28
Hi everyone,

I just bought a new external hard drive of 1TB from LaCie and i want to use it ;). I used gparted to format the entire hard drive with the ext3 filesystem (is there a better one for such large hard drive ?). Now, i obtain the following from the command line:

```
steeve@steeve-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc4bbc4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11918    95731303+  83  Linux
/dev/sda2           11919       12161     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e4f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x32570eef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5168    39070048+   c  W95 FAT32 (LBA)

```

So, my new hard drive is in /dev/sdb1 if i understand this. So i create a LaCie folder in /media in order to mount my HD with the following:
```
steeve@steeve-laptop:/$ sudo mkdir /media/LaCie
steeve@steeve-laptop:/$ cd /media
steeve@steeve-laptop:/media$ ls
cdrom  cdrom0  EULER  LaCie

```

Now, i mount my hard drive...
```
steeve@steeve-laptop:/media$ sudo mount -t ext3 /dev/sdb1 /media/LaCie/
steeve@steeve-laptop:/media$ 

```

And i manage to change the permissions so that i can create, delete etc without being a root user with
```
steeve@steeve-laptop:/media$ sudo chmod -R 777 LaCie/
steeve@steeve-laptop:/media$ ls
cdrom  cdrom0  EULER  LaCie
steeve@steeve-laptop:/media$
```

So, when i click on the desktop icon to access the content of my HD and right-click my mouse in order to create a folder, the menu is gray...i can't create anything...what i'm doing wrong here ?

Thanks

---

### Post by sisco311 on 2008-09-28
change the owner:
```
sudo chown -R $USERNAME: /media/LaCie/
```

---

