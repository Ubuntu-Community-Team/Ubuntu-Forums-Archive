---
title: "How to remove Windows from Ubuntu ?"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by User2011 on 2011-09-25
I installed Ubuntu in Windows XP computer and everything worked out okay. I am currently using Ubuntu 11.04 with problem free. I've decided I'm only going to use Ubuntu 11.04 from now on and I no longer wish to use Windows XP.. 

Everytime when I turn my computer pc on I have the option to use Ubuntu or Microsoft Windows XP. Can anybody please help me uninstall Windwos XP using Ubuntu 11.04 ?!

Thank you.

---

### Post by Mark Phelps on 2011-09-25
If you installed Ubuntu using Wubi, you installed that USING Windows -- and removing Windows will remove Ubuntu as well.

If you don't remember whether or not you did that, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That lists out the partitions on your drive.  If they are all Windows filesystems, then you installed via Wubi.

---

### Post by User2011 on 2011-09-25
I Believe I've installed Ubuntu 11.04 via Wubi because I downloaded Ubuntu on Ubuntu website and installed it through Windows. Due to that action, now I have a dual booting (Windows/Ubuntu) I want to delete Windows completely and only use Ubuntu! Windows is taking too much space of my disk and I'm not even using it anymore... Thanks for the tip, this is what I got as a result on my terminal:

> Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       80324       40131   de  Dell Utility
/dev/sdb2   *       80325   227801699   113860687+   7  HPFS/NTFS
/dev/sdb3       227801700   305893664    39045982+   7  HPFS/NTFS
/dev/sdb4       305893665   312496379     3301357+  db  CP/M / CTOS / ...

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02690268

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78895214    39447576    7  HPFS/NTFS
/dev/sda2        78895215   160810649    40957717+   f  W95 Ext'd (LBA)
/dev/sda5        78895278   160810649    40957686    7  HPFS/NTFS

---

### Post by mörgæs on 2011-09-25
After backing up your user files:

If you boot from the Ubuntu CD and install, you simply choose 'use entire disc for Ubuntu'. This will erase everything that is on the drive.

---

### Post by mosaic2s on 2011-09-26
or go for [COLOR=Red]grub-customizer[/COLOR] and keep ubuntu as the default and give 4 sec as boot select option. use windows partition for storage only. this way, it will work.

---

### Post by anewguy on 2011-09-26
You'd be much better off backing up everything you want to save, then completely install Ubuntu again from the CD as per mörgæs 2 posts back.  Wubi is usually just used as a test platform - if you like Ubuntu after using it in Wubi a while you should always perform a normal install of Ubuntu.  Keeping a Windows partition so you can run Ubuntu and changing the boot menu default and time out isn't the way to go.  You really don't want to be dealing with anything Wubi when you are done.

Dave ;)

---

### Post by technosysind on 2011-09-26
If you have installed via wubi then I believe you should take backup of all your date and then format your hard disk and make a fresh ubuntu installation using cd or usb flash

---

### Post by anewguy on 2011-09-28
> **technosysind said:**
> If you have installed via wubi then I believe you should take backup of all your date and then format your hard disk and make a fresh ubuntu installation using cd or usb flash

See my post above ;)

---

### Post by wildmanne39 on 2011-09-28
Hi, one other option is to migrate your wubi install to a normal install here is a link.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
Then you have to reclaim the space on the hard drive after you remove windows, just another option, I personally would do what anewguy suggested.
Thank you

---

