---
title: "Returning to Ubuntu"
date: 2019-03-11
forum: New to Ubuntu
---

### Post by nekojosh2 on 2019-03-11
Hi everyone! After a long time of been away I've decided to install Ubuntu again on my desktop in order to do some projects and what not (been away from the scene since 2011).
So, I'm having some issues installing Ubuntu 18.10, but not sure where is it that I'm failing. I think it might be related to the boot mode but not sure.
So here is my current setup: 
 1x m.2 SSD where Windows 10 is installed, that's my boot drive.
1x SATA Samsung SSD (currently blank, ntfs formatted and where I want Ubuntu to reside)
2x Western Digital Blue HDD in a RAID 0 arrangement using AMD-RAID solution.
The raid is managed by the mobo which is a Gigabyte GA-AB350-D3H

So I burned the Ubuntu ISO into a DVD and went ahead and booted that to install the OS. Once at the setup I'm only seeing the m.2 SSD and it's partitions. The Raid and the other SSD are not showing I can't pick them to install the OS.

Ultimately I'd like to have Ubuntu reside in the SATA SSD and Windows 10 ion the m.2 SSD and that they both see the RAID so I can place files in there since that's mostly storage.

My BIOS is currently set to UEFI and my boot driver is RAID, since well, I have a RAID 0 configured.

I'd appreciate any help in order to achieve this. Thanks in advance.

---

### Post by oldfred on 2019-03-11
Standard desktop does not install in RAID mode, we normally suggest changing to AHCI. A few motherboards let you have different settings for different drives, does yours?

Why even RAID 0 when you have fast SSDs?
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Have you tried the server installer? It includes RAID support and then you can add desktop of choice. You do not have to install most of the typical server software as one of last install steps is what you want to install. 
       
 [https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by mastablasta on 2019-03-12
though i am not sure if a server included the AMD RAID or if AMD raid is even supported under linux. And even if it is, is it supported with NTFS file system? 

in Linux you would use mdadm (software) raid. Benefit is that if your motherboard dies you can get an intel one and still able to access all the files. 

the whole setup the OP made looks problematic to me from the point that something can go wrong and you loose all the files. raid 0 is useless these days, unless you have small disks and need to create a large disk space.

raid 1 and above, also do not protect your data. this is done by regular, automatic, and scheduled backup. raids protect against disk loss, so that your server could still be operating even if one disk drive failed. this would give you time to replace the failed drive while still have access to data. 

if data get's corrupted on one disk that corruption is then mirrored to the others. so separate backup(s) is (are) the way to protect the data.

---

