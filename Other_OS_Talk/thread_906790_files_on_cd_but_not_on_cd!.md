---
title: "files on cd but not on cd?!?"
date: 2008-08-31
forum: Other OS Talk
---

### Post by anystupidname on 2008-08-31
OK, so this is getting on my nerves. I'm simply trying to update the BIOS on a system that won' t boot from USB and doesn't have a floppy drive, right? So I download a bootable ISO from [http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/Win98SEnoram_bootdisk.iso](http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/Win98SEnoram_bootdisk.iso)
and I inject the aflash.exe and bios image file into it, save it and write it to CDR / CDRW. The problem is, when I boot up with the CD and get to the DOS prompt, aflash.exe and the other file are not shown on the CD!!! I've reproduced this 3 times using different combinations of UltraISO/WinISO different burning apps and 2 CDRs and one CDRW... WTF? Any suggestions welcome.:confused:

---

### Post by pytheas22 on 2008-09-01
Are you sure that the files are really getting inserted into the ISO image properly?  You can check by opening up the ISO in Archive Manager to make sure they're there, and in the location that you expect.

---

### Post by anystupidname on 2008-09-01
Problem resolved: I never found out what was happening with the problem reading in DOS. Here is the way I finally ended up flashing the BIOS.

-installed unetbootin freedos
-using winimage, injected BIOS files into "c:\unetbtn\ubninit" (2.88MB floppy image)
-booted into freedos and flashed BIOS (hurray)
-rebooted to find boot record had been overwritten?!?
-booted to rescue DVD and repaired MBR...

> **pytheas22 said:**
> Are you sure that the files are really getting inserted into the ISO image properly?  You can check by opening up the ISO in Archive Manager to make sure they're there, and in the location that you expect.

Yea, I'm sure. Files present when ISO extracted. Files present when viewing CD not in DOS. Files present when viewing ISO in multiple tools...

---

