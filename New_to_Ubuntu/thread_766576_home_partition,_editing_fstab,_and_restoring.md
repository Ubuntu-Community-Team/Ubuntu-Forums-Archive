---
title: "/home partition, editing fstab, and restoring"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Paul133 on 2008-04-25
Yesterday, in preparation for downloading Hardy, I wanted to make sure I had a /home partition, which I had made sure to create when I installed Gutsy. Unfortunately, I looked in GParted (and fstab) and the partition was mounted at /media/sda7. So I edited the fstab file in nano (didn't make any back-up, not the best idea in the world) and changed /media/sda7 to /home. Success, kind of. The next time I logged in, the partition was mounted at /home and my computer had basically returned to November 16, 2007 (probably around the time I installed Gutsy). Everything in my home folder, all my documents, etc. were all from November 16 or earlier; I had lost everything done after that date and things I had since deleted were there again. Editing fstab to remount the partition at /media/sda7, though, restored my computer to what it had been last night. 

So, my questions are twofold: 1, what happened? why did fstab restore this old state? and 2, how should I mount this partition at /home?

---

### Post by Oldsoldier2003 on 2008-04-25
> **Paul133 said:**
> Yesterday, in preparation for downloading Hardy, I wanted to make sure I had a /home partition, which I had made sure to create when I installed Gutsy. Unfortunately, I looked in GParted (and fstab) and the partition was mounted at /media/sda7. So I edited the fstab file in nano (didn't make any back-up, not the best idea in the world) and changed /media/sda7 to /home. Success, kind of. The next time I logged in, the partition was mounted at /home and my computer had basically returned to November 16, 2007 (probably around the time I installed Gutsy). Everything in my home folder, all my documents, etc. were all from November 16 or earlier; I had lost everything done after that date and things I had since deleted were there again. Editing fstab to remount the partition at /media/sda7, though, restored my computer to what it had been last night. 

So, my questions are twofold: 1, what happened? why did fstab restore this old state? and 2, how should I mount this partition at /home?

could we see the output of
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Paul133 on 2008-04-25
sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10         861     6835937+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1315        5570    34179687+   7  HPFS/NTFS
/dev/sda4            5571        9729    33407167+   5  Extended
/dev/sda5            6179        9729    28523376   83  Linux
/dev/sda6            5571        5606      289107   82  Linux swap / Solaris
/dev/sda7            5607        6178     4594558+  83  Linux

Partition table entries are not in disk order

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d76bcd12-1102-4de0-ad91-b09c899b2d16 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-0218  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=9A98EF5898EF3185 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=36C8F354C8F3113B /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=455e0c1d-9da9-44fe-be70-91fed9345ac2 /media/sda7     ext3    defaults        0       2
# /dev/sda6
UUID=4c129ac7-a254-4ee1-b679-ab19997654bc none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I edited the 18th line, from "/media/sda7" to "/home" and then rebooted. After I saw it was restored, I edited it back to "/media/sda7" and it seemed fixed. I just don't understand why editing fstab would trigger that. Can't I just remount the partition?

---

### Post by Oldsoldier2003 on 2008-04-25
Weird behavior. usually when you edit the fstab all you need to do is 

```
sudo mount -a
```
for the changes to be picked up. But I'm glad all is working for you now.

---

### Post by Paul133 on 2008-04-25
Thanks for the help. I just hope I can find a way to mount my partition on /home so I can keep my settings and files when I do a clean install of Hardy.

---

