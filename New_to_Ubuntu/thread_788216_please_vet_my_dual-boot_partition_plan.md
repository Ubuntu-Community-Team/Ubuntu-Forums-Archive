---
title: "please vet my dual-boot partition plan"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by linuxgrrl on 2008-05-09
My dad is overhauling a 5 year old computer and would like to have it dual-boot with a fresh install of both XP and linux. I've reviewed the ubuntu dual-boot setup instructions but they seem geared to someone who already has XP installed, whereas I'm "starting fresh" so I combined those instructions with a 2006 how to found here: [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Here is my plan, please someone tell me if this is seriously flawed so I can avoid embarassing myself viz. Dad:

STEP ONE would be to use gparted to partition the drive as follows
 
10 GB to first primary partition for Winxp
15 GB to second primary partition for linux root directory [EXT3]
5 GB for linux /home directory [EXT3]
1 GB for linux swap partition [LINUX SWAP]
35 GB for shared data [NTFS]

STEP TWO would be to install WinXP to the first primary partition

STEP THREE would be to install Ubuntu at the second primary partition.

Remaining steps would proceed as normally stated in the Ubuntu dual boot documentation (i.e., use grub to boot, not take all the other steps in the other tutorial to use the windows boot loader).

Does this look right? Is NTFS the best/simplest file system for data that will be shared between both OS's?  Can I safely ignore the instructions in other tutoridals re: using weird things like "BootPart" and editing the boot.ini files in windows, and simply let Ubuntu take care of things?

Thanks

---

### Post by halitech on 2008-05-09
looks good to me but as a warning, NTFS was (still is?) cranky with writing from Linux so may want to go with FAT32 instead of NTFS although I've been using an external drive that is formated NTFS and so far no data corruption but I could be getting lucky so far

---

### Post by philinux on 2008-05-09
You only need about 8-10 gig for root. So you could use more for home.

Swap you might get away with less.

---

### Post by maybeway36 on 2008-05-09
I would suggest a little more for /home if there's room.
For the shared partition you might try ext3. The ext2 driver for Windows ([http://www.fs-driver.org/](http://www.fs-driver.org/)) will let you use Windows to read and write to it.

---

### Post by squee on 2008-05-09
I use ext 3 for my shared partition and that works fine. For Vista I had to get a little program that would allow ubuntu to recognise it, but now I have that, its a dream.

---

### Post by jimroby on 2008-05-09
> **linuxgrrl said:**
> My dad is overhauling a 5 year old computer and would like to have it dual-boot with a fresh install of both XP and linux. I've reviewed the ubuntu dual-boot setup instructions but they seem geared to someone who already has XP installed, whereas I'm "starting fresh" so I combined those instructions with a 2006 how to found here: [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Here is my plan, please someone tell me if this is seriously flawed so I can avoid embarassing myself viz. Dad:

STEP ONE would be to use gparted to partition the drive as follows
 
10 GB to first primary partition for Winxp
15 GB to second primary partition for linux root directory [EXT3]
5 GB for linux /home directory [EXT3]
1 GB for linux swap partition [LINUX SWAP]
35 GB for shared data [NTFS]

STEP TWO would be to install WinXP to the first primary partition

STEP THREE would be to install Ubuntu at the second primary partition.

Remaining steps would proceed as normally stated in the Ubuntu dual boot documentation (i.e., use grub to boot, not take all the other steps in the other tutorial to use the windows boot loader).

Does this look right? Is NTFS the best/simplest file system for data that will be shared between both OS's?  Can I safely ignore the instructions in other tutoridals re: using weird things like "BootPart" and editing the boot.ini files in windows, and simply let Ubuntu take care of things?

Thanks
I probably know less than you do,but I would give the data partition to XP.
That is just make the XP partition larger.Ubuntu can easly read and write to
the XP partition with out upseting XP.It used to be true that Windoz when it came to a non M$ partition would stop reading,and see nothing beyond.That may
not still be true,but it would be a real bust if Win couldn't see the data partition,which is beyond Ubuntu.Recently I worked on a busted win2k that would only load so far and then do cyclical reboots.I used the Ubuntu live CD to boot the machine and make a complete backup to a seperate drive before I wiped the Win2K.Ubuntu had trouble (most likely files marked hidden or system)with the actual Win2k system files,but then that for me was a boon since the sys was hosed.It copied all the user data and I was able to mine for it after reinstalling an OS

---

### Post by louieb on 2008-05-09
:KSI like it. What your planning is pretty close to how I have my machines partitioned. The Linux root partition can be a little smaller, mine are 7-10GB in size.     Give the extra space to your data partition or create a partition for a test install of the next version of Ubuntu.   

Since I use Linux 90% of the time my data partition is ext3. If I used XP more then I would have made it an NTFS file system.   For security and reliability reasons I don't use the fat file system. Even Microsoft doesn't recommend using it.

---

