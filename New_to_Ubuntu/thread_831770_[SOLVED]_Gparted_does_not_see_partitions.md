---
title: "[SOLVED] Gparted does not see partitions"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by exup1000 on 2008-06-17
Hi, I am a bit puzzled by Gparted, I have used partition magic and looked up the equivalent in Ubuntu, have installed it ok but when I run it, it just shows the whole of my drive as being unallocated.

The drive should have two partitions, XP and Unbuntu.
The drive is a new Solid State Drive so wonder if thats the issue.
I can see my other partition XP in file browser and can access files.

Please help as Ubuntu has consume all of the free space that was on the drive and when I am in XP I can no longer save files.

The drive is 60GB and Ubuntu consumed 35 GB.

Cheers Exup

---

### Post by housam on 2008-06-17
Are you able to boot both systems without problems ?
if so, try to use the Gparted live CD , It could help reading your drive.

---

### Post by justleen on 2008-06-17
on what disk is XP installed? SDA2 aswell?

can you post the output of 
```
 sudo fdisk -l
```

---

### Post by exup1000 on 2008-06-17
Hi

yes I can boot to both partitions no problems everything works fine. Install was pretty painless.

I have logged onto the Gparted site and downloaded the live CD and see if that can help. 
Will post back results

Cheers

---

### Post by exup1000 on 2008-06-17
Hi
here is the information from fdisk

Disk /dev/sda: 64.0 GB, 64023257088 bytes
240 heads, 63 sectors/track, 8270 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x8c158c15

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3345    25288168+   7  HPFS/NTFS
/dev/sda2            3345        8270    37234890    5  Extended
/dev/sda5            3345        8062    35656236   83  Linux
/dev/sda6            8062        8270     1574338+  82  Linux swap / Solaris


Cheers

---

### Post by justleen on 2008-06-17
at least fdisk is showing the correct partitions...so must be just gparted..

if you start gparted from a terminal, do you see any errors there?

---

### Post by exup1000 on 2008-06-17
Hi

I have booted to the beta version of live CD for Gparted 0-3.4-10, I can select the drive from the drop down list and shows same thing, 59GB all unallocated?

Will try their current live and stable version which is 0.3.6-7

Cheers

---

### Post by exup1000 on 2008-06-17
Hi Justleen,

good tip, and yes it states in the terminal, "Cant have overlapping partions"

Will google this on their website and see what turns up - unless you have some thoughts.

Cheers

---

### Post by justleen on 2008-06-17
hmm

checking you fdisk output again, nothing is overlapping

Besides,  Fdisk will be the first to let you know if anything is wrong...
Device    Start End 
/dev/sda1 1     3345 
/dev/sda2 3345  8270 --> extended
/dev/sda5 3345  8062 
/dev/sda6 8062  8270

---

### Post by housam on 2008-06-17
> **justleen said:**
> hmm

checking you fdisk output again, nothing is overlapping

Besides,  Fdisk will be the first to let you know if anything is wrong...
Device    Start End 
/dev/sda1 1     3345 
/dev/sda2 3345  8270 --> extended
/dev/sda5 3345  8062 
/dev/sda6 8062  8270

I think he has an overlapping problem as shown in his fdisk-l .
the partitions end at the same start cylinder of the next one while it should end just before the start of the next.

I mean that his table should look like that 
> Device    Start End 
/dev/sda1 1     3345 
/dev/sda2 334[COLOR="Red"]6[/COLOR]  8270 --> extended
/dev/sda5 334[COLOR="red"]6[/COLOR]  8062 
/dev/sda6 806[COLOR="red"]3[/COLOR]  8270

---

### Post by exup1000 on 2008-06-17
I had a search around and it seems testdisk is good at fixing overlapping errors.
Have installed it and run through the analyse mode. It reports incorrect number of heads so proceed and then write changes.
At reboot can log in to both partitions ok and this time when i run gparted it can see the partitions!!
Cannot change them though have to use live CD which I am running now as I type, fingers cross it works?

---

### Post by exup1000 on 2008-06-17
All is good, after running the testdisk and booting to the live CD version of Gparted, I could succesfully move around my partitions and resize them. 
I now have a 60GB divided up with XP on 45 GB and Ubuntu on 15GB.

Many thanks to all above who gave enough information to head me off in the right direction.

Cheers

---

