---
title: "Grub Error 18 - Boot loader trouble"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by graben3 on 2008-08-25
I had a power surge anbd my grub bootloader display error 18

I cant access either my xp partition or my ubuntu 8.04 partition

I thought of addung a new hd and installing ubuntu on it to automatically change the hds where grub ad installed its stuff on.

Do you think this will work? Im asking you this because I cannot afford to loose some data...

Please tell me if you did this and were successfull for the same situation

---

### Post by alienexplorers on 2008-08-25
Grub error 18

info grub wrote:
18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

You could have a bad block on your file system.  Run fsck to check it out.

---

### Post by Patb on 2008-08-25
Graben, rather than adding a new HD, why not boot from a live CD and see if you can mount the drive which is giving you problems.  First step if you can would be to back up the data you "cannot afford to lose" perhaps to a USB drive.  Then you could run the diagnostic test suggested by Alienexplorers.

If data recovery becomes difficult because of corruption, try testdisk which is in the repositories or you could use [Photorec]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/"). 

Whatever you use, check the man or info page first, as Alienexplorers has hinted.

Hope this helps.  Cheers, Pat.

---

### Post by graben3 on 2008-08-25
> **alienexplorers said:**
> Grub error 18

info grub wrote:
18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

You could have a bad block on your file system.  Run fsck to check it out.


I have 4 HDs, 2x250GB, 1x320GB and 1x120GB. They were all working correctly and had the right size in my Bios and Grub was working perfectly before the power surge...

Its definitively something that has to do with bad blocks on HD or something like this...

Ill try the live CD in case I can repair or reinstall GRUB with it...

---

### Post by graben3 on 2008-08-25
> **Patb said:**
> Graben, rather than adding a new HD, why not boot from a live CD and see if you can mount the drive which is giving you problems.  First step if you can would be to back up the data you "cannot afford to lose" perhaps to a USB drive.  Then you could run the diagnostic test suggested by Alienexplorers.

If data recovery becomes difficult because of corruption, try testdisk which is in the repositories or you could use [Photorec]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/"). 

Whatever you use, check the man or info page first, as Alienexplorers has hinted.

Hope this helps.  Cheers, Pat.


First, thank you all for your support

I booted from a live CD (during the boot with the live CD a lot of errors about my SDD1 device shown on a black screen. Bad blocks & etc...) It finally booted and I noticed my SDD1 HD was not mounted automatically like my other 3 HDs.)

Then I runned fsck on the HD that I thought was the problem (SDD1)... 

It had a lot of errors on it so I was kind of skeptic it would ever be OK...

And WOWWWWW ! magically my grub menu works again and I did not lose anything as far as I can see !

Special thanks to Alienexplorer and Patb !

---

