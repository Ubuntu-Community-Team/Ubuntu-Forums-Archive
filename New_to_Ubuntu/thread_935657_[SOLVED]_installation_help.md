---
title: "[SOLVED] installation help"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by n5kb on 2008-10-01
Howdy from Texas

I like Ubuntu enough I have decided to put it on my laptop. 

1st Question: I want to use DriveImage to back up my files before I attempt installation. This laptop has no floppy drive and that is how I would normally start DriveImage. Any DriveImage experts out there??

2nd question: Assuming I can get past the 1st problem I want to partition my hard drive half for XP and half for UBUNTU. Is it possible to boot to the 2nd patition with Ubuntu?? How many partitions do I need and what types? as in hda ect?

3rd Question:  Is there a list of laptops that have already successfully had Ubuntu installed on them? I did a search for mine with no results.

Thanks in advance for any info
N5KB

---

### Post by tuxxy on 2008-10-01
2. You need 2 partitions I would install windows first then Ubuntu, you should see them both listed at boot in your GRUB menu, heres a guide on [partitioning]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html")

[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

3. [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by Paqman on 2008-10-01
> **n5kb said:**
> 
1st Question: I want to use DriveImage to back up my files before I attempt installation. This laptop has no floppy drive and that is how I would normally start DriveImage. Any DriveImage experts out there??


You could boot up into the LiveCD and try one of the Linux imaging apps, like PartImage. Alternatively, try the Clonezilla LiveCD.

> 
2nd question: Assuming I can get past the 1st problem I want to partition my hard drive half for XP and half for UBUNTU. Is it possible to boot to the 2nd patition with Ubuntu?? How many partitions do I need and what types? as in hda ect?


The installer can create the partitions for a dual-boot setup for you automatically. Alternatively use the Wubi installer to set up the dual-boot without creating any partitions (it creates a virtual hard drive on the Windows partitions and installs Ubuntu there)

If you want to do the partitioning yourself then shrink your Windows partition down to about 20-30GB, create a "swap" partition the size of your RAM, and then create an ext3 partition for the Ubuntu root (written as /)

> 
3rd Question:  Is there a list of laptops that have already successfully had Ubuntu installed on them? I did a search for mine with no results.


Yes, [there is](https://wiki.ubuntu.com/LaptopTestingTeam). Some of those reports are more current than others, though. By far the best way to answer the question is to boot into the LiveCD and test your hardware yourself.

---

### Post by jimrz on 2008-10-01
why don't you post you laptop specs (make / model / video card / wifi card, etc) so that others with similar equip can give you an idea what you may expect.

---

### Post by n5kb on 2008-10-02
The laptop is HP Pavillion ZE4906 US
              1gb ram
              160 GB Hard drive

I will post results when I have them. Ububtu or bust!!

N5KB

---

### Post by n5kb on 2008-10-02
Ubuntu installed just fine. It had a kernel panic but we got past that. The sound was bad. The wired ethernet worked ok. The wireless lan did not work (cisco pcmia card) I have uninstalled ubuntu and downloaded DamnSmall. It works ok except very slow.

N5KB

---

### Post by intimatewipe on 2008-10-02
while DSL is a good product mate you would have been better off trying a bit with ubuntu,with a gig of ram/160gigdrive you would have been well set up,you could of found/bought a wireless card or usb device to get that on the couch thing going and as for the sound It would have paid to look at some of the help threads on this forum,they are excellent and most probs are surmountable with a bit of effort,give it another go,if you like install xp and dual boot with ubuntu,just spend a bit of time looking at tutorials,ubuntu with the eyecandy switched on is very sweet,good luck with it

---

