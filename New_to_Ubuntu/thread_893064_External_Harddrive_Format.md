---
title: "External Harddrive Format?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Jeenyus on 2008-08-17
I just bought a 250GB Maxitouch 4 external HDD.  Its formatted as HPFS/NTFS.  I currently dual boot XP/Hardy and have a separate FAT32 partition for all my music and what not which is what I am moving over to the External HDD.  My question is should I format the External HDD to FAT32 or will it be fine leaving it as is.

Thank you,
Jeenyus

---

### Post by carlinuxlearner on 2008-08-17
Files have nothing to do with the file system they are in, if it was on a (lets just say) ext3 file system, it can be copied to a NTFS, FAT16, FAT32, or zfs filesystem without changing a thing.

C@RL

So what I'm saying is, it's fine, you can leave it how it is, unless you have some reason to change it (like, say you wanted to connect it to a win98 computer).

---

### Post by Rolcol on 2008-08-17
It depends what you're going to be using the hard drive for.  Ubuntu can handle NTFS fine unless there's an unclean removal which then you have to force mount the drive through the terminal.  If you format to FAT32, you will only have a 4GB file size limit.  You can format it as ext3 and install software on windows to be able to recognize/use ext3.

---

### Post by Jeenyus on 2008-08-18
Thank you both.  I left it as NTFS and compied all my music to it and it seems to be working fine.  I was woried about the compatability with ubuntu but I think thats an outdated issue and ubuntu is now about to read/write to NTFS fine.  Thanks again.

---

### Post by psychomichael on 2008-08-18
can anyone tell me how to format an external drive to ext3? I just bought a Klegg 250GB drive and it won't mount.

---

### Post by halitech on 2008-08-18
use gparted (System - Administration - Partition Editor) to check and see if its there. You can also open a terminal and type in 
```
sudo fdisk -l
```

---

### Post by psychomichael on 2008-08-18
Thank you! After searching around a bit more, I found a thread dedicated to my question...

[http://ubuntuforums.org/showthread.php?t=856061](http://ubuntuforums.org/showthread.php?t=856061)

---

