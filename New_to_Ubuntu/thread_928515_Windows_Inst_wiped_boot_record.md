---
title: "Windows Inst wiped boot record"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-09-24
So I did kind of anticipate this, but thought it could be remedied by perhaps a grub reinstall or something.. But.. uhh.. is this possible? I'm using ext2fsd to access my linux drives from windows, so if all else fails I could back up and re-install but.. would be cool if I could just reactivate the grub loader..

Any clues?
Thanks for considering!

---

### Post by Peter09 on 2008-09-24
Yes, this is possible. I think one of the recommended methods is to use the supergrub disk which can be downloaded from the Ubuntu download site.

---

### Post by Paqman on 2008-09-24
Easily done, no need to brun extra CDs. The LiveCD can do the job for you.

[How to restore Grub](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by Orange_and_Green on 2008-09-24
Yes, it's possible to just re-install Grub to the MBR!:)

Boot Ubuntu from a live cd, then please post the output of ```
sudo fdisk -l
```

Or follow this guide:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Good luck

[EDIT]Third!!:)

---

### Post by hungryOrb on 2008-09-24
Thanks.. You guys are heroes.. !:guitar:

---

### Post by hungryOrb on 2008-09-24
> **Orange_and_Green said:**
> Yes, it's possible to just re-install Grub to the MBR!:)

Boot Ubuntu from a live cd, then please post the output of ```
sudo fdisk -l
```

Or follow this guide:

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

Good luck

[EDIT]Third!!:)

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e76c254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48829536   83  Linux
/dev/sda2            6080        9726    29294527+   5  Extended
/dev/sda3   *        9727       19456    78156225    7  HPFS/NTFS
/dev/sda5            6080        6140      489951   83  Linux
/dev/sda6            6141        7356     9767488+  83  Linux
/dev/sda7            7357        9726    19036993+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


Thanks :D
Couldn't find stage1.

---

### Post by hungryOrb on 2008-09-24
> grub> find /boot/grub/stage1

Error 15: File not found

grub> 


Hmm.. I missed an instruction, right?

---

### Post by Idefix82 on 2008-09-24
If you have a separate boot partition, try /grub/stage1 instead of /boot/grub/stage1.

---

### Post by Idefix82 on 2008-09-24
Did you try the second edit in the first post in the link provided?

---

### Post by hungryOrb on 2008-09-25
> **Idefix82 said:**
> If you have a separate boot partition, try /grub/stage1 instead of /boot/grub/stage1.

Thanks Idefix, that worked :D
It returned (hd0,4) I think, and so I used that in the root and setup commands, but actually, nothing happened :D Or rather, grub didn't load at boot, only windows still! 
But I think it's progress! Thanks :D

---

### Post by hungryOrb on 2008-09-25
Uhhh.. Is it possible that running this from Live CD is the problem?

---

### Post by kansasnoob on 2008-09-25
Well, looking at this I'm curious:

> Device Boot Start End Blocks Id System
/dev/sda1 1 6079 48829536 83 Linux
/dev/sda2 6080 9726 29294527+ 5 Extended
/dev/sda3 * 9727 19456 78156225 7 HPFS/NTFS
/dev/sda5 6080 6140 489951 83 Linux
/dev/sda6 6141 7356 9767488+ 83 Linux
/dev/sda7 7357 9726 19036993+ 82 Linux swap / Solaris

Do you know what your partitions are?

I can see that sda1, sda5, and sda6 are all Linux but do you know which is which?

I'm also a tiny bit concerned that Windows may be in the extended partition (sda2) but since windows boots I think it's OK.

In answer to your last question you should be using the Live Cd at this point.

---

### Post by hungryOrb on 2008-09-25
> **kansasnoob said:**
> Well, looking at this I'm curious:



Do you know what your partitions are?

I can see that sda1, sda5, and sda6 are all Linux but do you know which is which?

I'm also a tiny bit concerned that Windows may be in the extended partition (sda2) but since windows boots I think it's OK.

In answer to your last question you should be using the Live Cd at this point.

Thanks :)
I am not certain about the partitions, but I know I have a huge useless swap partition, and some others which don't make sense!
Actually, at this point, I guess I'd just like to cut and paste a whole load of files and then just reformat those partitions into 2, for a fresh ubuntu. The old ubuntu seemed to have been playing up a little..

---

### Post by Sef on 2008-09-25
> I am not certain about the partitions, but I know I have a huge useless swap partition, and some others which don't make sense!
Actually, at this point, I guess I'd just like to cut and paste a whole load of files and then just reformat those partitions into 2, for a fresh ubuntu. The old ubuntu seemed to have been playing up a little..

That sounds like a good idea.  Sometimes a clean reinstall is the easiest and best solution.  Swap should not be more than 1 GB.

---

### Post by Idefix82 on 2008-09-25
> **Sef said:**
> Swap should not be more than 1 GB.

Really? I thought it had to be at least the size of your RAM if you want to be able to suspend because the RAM is just written into the SWAP partition.

---

### Post by hungryOrb on 2008-09-26
> **Idefix82 said:**
> Really? I thought it had to be at least the size of your RAM if you want to be able to suspend because the RAM is just written into the SWAP partition.

Thanks guys.. I'll head for this solution. =)

---

