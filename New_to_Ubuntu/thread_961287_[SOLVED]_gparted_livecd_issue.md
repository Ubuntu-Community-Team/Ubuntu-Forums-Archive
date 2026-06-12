---
title: "[SOLVED] gparted livecd issue"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by economy on 2008-10-28
I think I hit the [solved] button a little too early before...

I'm dual booting with Vista installed first, and would like to decrease the partition size of Vista in order to create another /home partition with the extra space... I have downloaded and burned the .ISO for the gparted live cd, but when I restart the CD doesn't boot, it just brings me to the menu to select Vista or Ubuntu... and of course I can't work with the partition while using Ubuntu because Vista and Ubuntu are sharing the same HD... 

any ideas on how I can make the live CD boot? I know this is probably extreme beginner stuff...

---

### Post by jespdj on 2008-10-28
1. Look in the BIOS settings of your computer, check if it is setup so that it tries to boot from the CD/DVD drive before it tries to boot from the harddisk.

2. Did you burn the ISO correctly? It will not work if you simply put the ISO on a CD as a file; you'll need to burn it as an image to a CD.

---

### Post by bumanie on 2008-10-28
Did you install ubuntu via a live cd or the alternate cd? If you used the ubuntu live cd, it is unlikely that it is a bios issue unless you have since changed any settings in your bios. Vista has its own partitioner and is better at shrinking vista partitions than gparted is. Right click computer -- choose manage -- then choose storge devices. Right click on the vista partition and choose shrink from the drop down menu. You can use gparted from the live ubuntu cd, or double check that the gparted .iso you tried to burn was burned as an image and not burned as a data disc.

---

### Post by economy on 2008-10-30
Wow,

Ok... I had installed Wubi instead of setting up a dedicated partition, so when I did get the CD to boot, it showed one big partition that was of course mounted. I wound up reinstalling Ubuntu from the livecd, which meant repartition, but the repartition failed and wiped the whole laptop clean... luckily I had my data backed up! 

Thanks for your help, I got severely mixed up though.

---

