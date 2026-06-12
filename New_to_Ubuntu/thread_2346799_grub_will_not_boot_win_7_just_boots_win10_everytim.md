---
title: "grub will not boot win 7 just boots win10 everytime"
date: 2016-12-18
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-12-18
i have 2 2tb hard drives
one has windows 10 and lubuntu 16.04 and the other windows 7
sda1 is my new drive with windows 10 and lubuntu installed ( fresh install a few months ago)
sdb1 is my old windows 7 installed ( my old install of windows that i put back into the computer as i found an old game that will not run on win10)

grub finds all the operating systems but only boots lubuntu and windows 10
when i pick windows 7 it just boots windows 10

i have updated grub and it finds everything right where it should be
but just fails to boot windows 7 with windows 10 coming up each time

i can boot the second drive from bios and windows 7 boots fine..

how can i fix this?

drive sda1 is partitioned
windows 10
ubuntu 
swap
ntfs drive


drive sdb1  is partitioned
winreserved
win7
ntfsdrive

---

### Post by mastablasta on 2016-12-19
is Windows 7 using it's own boot loader or is it using the Windows 10 bootloader? if there is a windows boot loader on sdb1 then it would use that one.

windows 10 boot loader should also see windows 7 on PC. windows boot loader used to be accessed uisng F8. not sure if this is still the case.

---

### Post by yancek on 2016-12-19
If I understand correctly, you installed windows 10 and Lubuntu on one hard drive, then later attached another hard drive with windows 7 on it.  Is that the case?  Are windows 10 and Lubuntu installed using EFI?  Is the older windows 7 using MBR?  Sounds like that could be the problem.  Probably the best thing to do is to get the boot repair software and download it on Lubuntu and run it.  Make sure you select the option to Create BootInfo Summary and not try any repairs and then post a link to the output here.  Make sure both drives are attached before you run it.  This should provide enough information for someone to help you.    

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by a.dusty.trail on 2016-12-19
> **yancek said:**
> If I understand correctly, you installed windows 10 and Lubuntu on one hard drive, then later attached another hard drive with windows 7 on it.  Is that the case?  Are windows 10 and Lubuntu installed using EFI?  Is the older windows 7 using MBR?  Sounds like that could be the problem.  Probably the best thing to do is to get the boot repair software and download it on Lubuntu and run it.  Make sure you select the option to Create BootInfo Summary and not try any repairs and then post a link to the output here.  Make sure both drives are attached before you run it.  This should provide enough information for someone to help you.    

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

you are correct, both are mbr and not efi
windows 10 and ubuntu was installed with out the windows 7 drive  in the computer
windows 7 drive was installed with out the windows 10 drive in the computer and put back in after.

the computer is offline and the only internet access is my android tablet

---

### Post by yancek on 2016-12-19
You forgot to post the link to the boot repair output.

---

### Post by a.dusty.trail on 2016-12-21
> **yancek said:**
> You forgot to post the link to the boot repair output.

no i didnt ..
i mentioned that the machine is offline (no network drivers)so i cant download it and install it for ubuntu..and the boot disk is 2 years old, the source forge download page just hangs forever, is it even being maintained ?

so if it cant be fixed with what came on the install cd or with something that will not put me in dependency hell 
then im out of luck.. and ill consider it just broken and unable to distinguish between windows 7 and win10
which is just silly in a long term support system

---

### Post by oldfred on 2016-12-21
It is normally just a Windows issue.

With BIOS Windows only boots from the drive set as default in BIOS and the the one primary NTFS partition with the boot flag.
Multiple installs of Windows then typically only have one BCD in boot partition that has entries for all Windows installs.

If you separate your Windows installs and run Windows repairs on each of them so both installs have bootmgr & BCD then grub2's os-prober can find both as that is what os-prober looks for, not boot flag and BCD that Windows uses.

Also make sure NTFS does not need chkdsk, nor is hibernated. Windows 10 fast start up is always hibernated, so make sure it is off. Grub only boots/finds Windows that is not hibernated, nor needs chkdsk.

You may be able to do the same with a Windows repair/recovery disk. But set BIOS first to boot one drive, and set boot flag on primary NTFS with install. Then run repairs. Then switch BIOS to other drive and run repairs. You may then have to reinstall grub to one drive.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

