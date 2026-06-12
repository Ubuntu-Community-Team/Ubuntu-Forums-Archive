---
title: "Can Ubuntu defrag or clean up the file system?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by dfp10 on 2008-06-13
I run Ubuntu 8.04 on a the first SATA 60 GB hard drive. On startup I have been getting failure of reading of this drive and reverting to the second SATA hard drive software. The first drive is not showing up in the BIOS display. 
After complete shutdown and pressing on the hd data and power connections SATA 1 is recognized and Ubuntu starts normally.
These drives and the mother board are only 6 months old so I wonder if there is file system corruption on SATA 1.
Does Ubuntu have a file system inspection or defrag facility?
Tnanks
Don Parsons [email]dfp10@capital.net[/email]

---

### Post by gr4nf on 2008-06-13
fsck -f may help.

---

### Post by jordanmthomas on 2008-06-13
```
sudo touch /forcefsck
``` and your partition will be checked the next time you mount it (boot, most likely)

After it checks you may want to remove /forefsck or it'll do it again next time.  I'm not sure if it'll remove itself when the check is done or not (and I use jfs so it may not be the same)

---

### Post by SunnyRabbiera on 2008-06-13
you really dont need defrag in linux, however the command gr4nf gave you is useful if you are getting filesystem errors.
But its possible this is a bad hard disk drive, age dont matter if the unit is defective.
what is the make and model of the HDD that is giving you issues?

---

### Post by stchman on 2008-06-13
> **dfp10 said:**
> I run Ubuntu 8.04 on a the first SATA 60 GB hard drive. On startup I have been getting failure of reading of this drive and reverting to the second SATA hard drive software. The first drive is not showing up in the BIOS display. 
After complete shutdown and pressing on the hd data and power connections SATA 1 is recognized and Ubuntu starts normally.
These drives and the mother board are only 6 months old so I wonder if there is file system corruption on SATA 1.
Does Ubuntu have a file system inspection or defrag facility?
Tnanks
Don Parsons [email]dfp10@capital.net[/email]

That sounds like a hardware problem.  File system fragmentation would have nothing to do with the BIOS not being able to recognize the hdd.

---

### Post by dca on 2008-06-13
> **stchman said:**
> That sounds like a hardware problem.  File system fragmentation would have nothing to do with the BIOS not being able to recognize the hdd.

+1
 
If you're getting a 'the drive works some time' or 'works to a certain point' it could be the logic board on the HDD itself or possibly one of the R/W heads on the platter has crashed but the others still work...

---

### Post by dfp10 on 2008-06-14
> **SunnyRabbiera said:**
> you really dont need defrag in linux, however the command gr4nf gave you is useful if you are getting filesystem errors.
But its possible this is a bad hard disk drive, age dont matter if the unit is defective.
what is the make and model of the HDD that is giving you issues?

It is Western Digital WD1600JS-00NCB1  (SATA)
Thanks
Don

---

