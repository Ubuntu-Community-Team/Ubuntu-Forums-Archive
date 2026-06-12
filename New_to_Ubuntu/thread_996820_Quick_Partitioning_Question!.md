---
title: "Quick Partitioning Question!"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Mudguard on 2008-11-29
Hello All,
I'm in the middle of partitioning my laptop using the windows xp set up cd. I had a dual boot with a smaller ubuntu space but want to repartition for an even amount of space for ubuntu and xp with a fat32 shared area inbetween. In the windows partitioning set up, to repartition to the set up i want i'm to delete the current partitions.. 

I'm just a bit unsure! am i to delete all partitions to repartition the way i want or is there a swap partition that i shouldn't touch?
Would the swap partition be shown here!
There is a small partition of 78mb, another of 1043mb, another 3224mb, then theres the bigger ones: 53945mb and 16402mb.

Should i leave those small ones and just divide up the 2 big ones up!? 
Any help would be much appreciated...

---

### Post by Scarlath on 2008-11-29
If I were you I'd make some free space up in GParted in Ubuntu, then just install Windows to that space. That way you wont have to worry about choosing the wrong partition. :)

---

### Post by mistafoxz on 2008-11-29
good question!

if you are planning on creating new installs for both os's, it would be easiest to simply migrate data to one partition, note the size of the drive (to avoid confusion during partitioning) and simply remove the remaining partitions.  Then, create one partition in the xp install (NTFS) of whatever size you want.  I recomend at least 10gb to ensure proper virtual memory allocation, plus room for apps.  once you are done with xp, ubuntu is very cool about recognizing your xp os and will migrate your settings.  also, the ubuntu installer has a great partitioner. use "manual" create your main partition with the ext3 file system and create another that is about double your physical memory. choose "swap" as the designation for this one.  
if you are trying to make a new install, watch out because the xp partition tool is a hammer, not a scalpel.  it will not move data or adjust things.  I would reccomend using the partitioner within ubuntu for these tasks, although you need an expert to tell you how to do it when you need to resize your main .ext3 drive while it is in use.  easier to load the "live" cd and do the operation from within the tryout environment.

hope this helps! just went through the same thing yesterday, so it is all pretty fresh!

E

---

### Post by Mudguard on 2008-11-29
Thanks for that mistafoxz!
I had gone ahead anyway ive left a small bit so i'll make that the swap partition when i install ubuntu, if it isn't enough i'll just start all over again!..

---

