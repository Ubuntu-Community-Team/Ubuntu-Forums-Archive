---
title: "Marge Root and home partitions"
date: 2021-04-07
forum: New to Ubuntu
---

### Post by ganganatha on 2021-04-07
I am fairly new to Linux and loving the KDE Neon.  I recently installed Kde and have this issue with home and root partitions. While installing i might have mistakenly allocated a larger size for root partition and smaller size for Home. Is there a way to switch or marge them together.  Or otherwise add more space to home.

My personal files and downloads are saved in Sda 7 = home partition. 
Sda 5 is the root KDE neon installed partition.
```

/dev/sda1        2048     534527    532480   260M EFI System
/dev/sda2      534528     567295     32768    16M Microsoft reserved
/dev/sda3      567296  539183168 538615873 256.9G Microsoft basic data
/dev/sda4   539185152  540207103   1021952   499M Microsoft basic data
/dev/sda5   540207104 1008934911 468727808 223.5G Linux filesystem
/dev/sda6  1008934912 1009983487   1048576   512M Microsoft basic data
/dev/sda7  1012031488 1032511487  20480000   9.8G Linux filesystem
```

---

### Post by CatKiller on 2021-04-07
> **ganganatha said:**
> While installing i might have mistakenly allocated a larger size for root partition and smaller size for Home. Is there a way to switch or marge them together.  Or otherwise add more space to home.

It's pretty straightforward to change the size of partitions.

You can't change a partition that's mounted, and if you're trying to run a partition editor from it then it's necessarily mounted. However, your live installer has a partition editor (so that you can set up your partitions during the installation process) and it doesn't matter if *that* is mounted while you're editing other partitions.

So the first thing to do (well, second: back up anything important first, just in case) is to boot into your live USB and start up the partition editor. Different flavours will have different tools by different names, but they'll all have a partition editor of some kind.

Then make your / partition smaller. Then make your /home partition bigger into the unallocated space that you just freed up.

From your listing, you have a 512 MB "Microsoft basic data" partition that might be between them, which will get in the way. If it is between them you can either delete it - if you know what it is and that you don't need it - or slide it along as part of your resizing process - if you don't know what it is, or know that you do need it.

---

### Post by coffeecat on 2021-04-07
@ganganatha, I've added code tags to your terminal output, which have restored the columnar formatting that was lost by posting without code tags. Please use BBCode code tags when posting terminal output, code, or contents of config files. Link in my sig if you need it.

---

### Post by yancek on 2021-04-07
It would probably be easiest to simply copy your data on the /home partition to the current / (root filesystem) partition.  Test to make sure all works as expected and delete or format the small (sda7) current /home partition.  One problem as pointed out above is that you have a windows partition between your two Linux partitions.  From the partial output you posted it is not possible to tell if there is any unallocated space to use to enlarge /home on sda7.  If you do want separate partition, the explanation in post 2 should work.

---

### Post by rsteinmetz70112 on 2021-04-07
You can change the size of file systems using gparted but in order to increase the size of a filesystem it needs adjacent unallocated space, that sometimes involves relocating other file system like your /dev/sda6 which seems to be a Windows partition. Generally people recommend 20-50GB from the root filesystem (/) and as much as you can get for your /home.
How? much data in in your / filesystem? It's probably pretty empty.

---

### Post by TheFu on 2021-04-07
For my reference - you know column headers would have been nice:
```
/dev/sda1        2048     534527    532480   260M EFI System
/dev/sda2      534528     567295     32768    16M Microsoft reserved
/dev/sda3      567296  539183168 538615873 256.9G Microsoft basic data
/dev/sda4   539185152  540207103   1021952   499M Microsoft basic data
[COLOR="#FF0000"]/dev/sda5   540207104 1008934911 468727808 223.5G Linux filesystem[/COLOR]
[COLOR="#EE82EE"]/dev/sda6  1008934912 1009983487   1048576   512M Microsoft basic data[/COLOR]
[COLOR="#FF0000"]/dev/sda7  1012031488 1032511487  20480000   9.8G Linux filesystem[/COLOR]
```

sda2, 3, 4 are fine.  sda6 is in a problem location. It would be best to move that right up against sda4.

You can't really switch the 2 Linux partitions purposes because 10G is too small for the OS these days.  Really, the OS partition needs to be 25-35G due to bloat in Ubuntu.  An Ubuntu Server without any GUI could run in 10G, however. But being you are new, that isn't something you will be ready to attempt for a year or more.
Because of how the storage is laid out, you are kinda screwed as a beginner.  I'd say your best option is to 
[LIST=1]
[*]delete both Linux file systems (sda5, sda7), 
[*]move sda6 immediately next to sda4, then 
[*]do a Linux install into the free space.  
[/LIST]
Order matters.  Probably want to backup all data that you cannot lose, not just Linux, but for Windows too, since this is high risk for mistakes.

I'm not a fan of dual booting, especially for someone new to Linux.  There are so many things that can go wrong - caused by two different OS boot systems fighting over who has patching for the booting areas.  Lots of people do dual boot and only have problems about once a year, so it isn't that bad, unless you don't have time to fix it when those problems arise.

For people new, I'd rather see you use virtual machines for a year or so to get used to seeing Linux storage name, mapping those names to file systems, and just becoming used to the Unix way things work. Running under a VM means you won't be gaming in Linux, assuming you keep Windows as the hostOS.  But you will be able to use pretty much everything else and it will work fine-to-good, depending on the hardware, RAM, CPU, disk, and VM tuning choices.

---

