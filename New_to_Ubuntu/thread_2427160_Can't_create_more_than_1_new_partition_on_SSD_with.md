---
title: "Can't create more than 1 new partition on SSD with Win10, free space marked&quot;unusable&quot;"
date: 2019-09-18
forum: New to Ubuntu
---

### Post by jellicus on 2019-09-18
I'm setting up a dual boot, and I shrank the windows partition on the 120gb SSD to free up 57Gb (I have a 2 Gb HD for all my data), and then created a new 35Gb partition for Linux in the installation dialog. So far so good, but now the remaining 22Gb I was going to use for the swap is marked "unusable". I can't create a primary or logical volume. Is windows using so many partitions it's maxed out? What's the issue?

[IMG]https://i.imgur.com/VXfuTYr.png[/IMG]

---

### Post by TheFu on 2019-09-18
MBR partitions have a limit of 4 primary partitions. This rule has been around since 1980.
A work-around was created in the 1980s, logical partitions.  But logical partitions only fit **inside** an "extended primary partition".  That 4th partition, should take up ALL the remaining storage and be marked as "Extended", then you can create a 25G "logical partition for Linux and a 4.1G swap logical partition. Both have to be completely contained inside the "extended partition".  

There are other options.
You can use a "swap file" if you like.
or
you could wipe the entire disk and change from MBR partitioning to GPT partitioning.  GPT supports over 100 "primary partitions" and does some other nice things. This requires reinstall of all OSes on the disk.  How good are your backups?

There are wikipedia articles about all this stuff. I bet those will explain it better than I could.
[https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
[https://en.wikipedia.org/wiki/Master_Boot_Record](https://en.wikipedia.org/wiki/Master_Boot_Record)
[https://en.wikipedia.org/wiki/Partition_type](https://en.wikipedia.org/wiki/Partition_type)

---

### Post by Impavidus on 2019-09-18
Using [s]BMR[/s] MBR partitioning (and that's what you use, and you can't change that without reinstalling Windows), you can have at most 4 primary partitions, or 3 primary partitions and a number of adjacent logical partitions. The logical partitions are in fact contained in an extended partition, which is itself a primary partition. So you should create your /dev/sda3 (the root partition) as a logical partition.

BTW, a 22GB swap partition is excessively large, unless you have 20GB ram and want to use hibernation. I'd suggest about 2GB swap. And besides, Ubuntu nowadays uses a swap file by default, but if you create a swap partition, it will use that.

---

### Post by jellicus on 2019-09-18
Thanks to all.  So, is the easiest thing at this point to let Ubuntu use a swap file rather than bother with a partition? Or should I go back and create a primary and 2 logicals? I'm not perfectly clear on how to do that in the software, but I'm assuming it won't be hard. I also assume I don't need to create a data partition on the SSD if I already have it on my HD.

> **Impavidus said:**
> 
BTW, a 22GB swap partition is excessively large, unless you have 20GB ram and want to use hibernation. I'd suggest about 2GB swap. And besides, Ubuntu nowadays uses a swap file by default, but if you create a swap partition, it will use that.

The tutorial I was using said a swap partition 2x the ram was recommended, and there's 8Gb.

---

### Post by The Cog on 2019-09-18
If it were me, I would delete sda3 and replace it with an extended partition that uses all the space between sda2 and sda4. Then you can create a few logical partitions (they number sda5 upwards and will always be inside the extended partiton). That does mean reinstalling Ubuntu though.

---

### Post by TheFu on 2019-09-18
Lots of good advice above.  Which is best is really a judgement call.  I would go with The Cog's method.  To do it, boot into Windows and do all the partition work inside there. Backup any Linux data you don't want to lose.  

The 2x RAM for swap sizing from from when systems had 1GB of RAM or less. I think it is bad advice for any system these days.

I have an 8GB desktop and a few others with less RAM; 2G, 4G and 6G.  2G isn't swap isn't enough for a desktop.  Modern browsers need more. Without sufficient swap, I've had system-wide slowdowns and lockups.  4G has been the smallest swap that works by providing sufficient feedback  (the system gets slower), before the system halts for lack of RAM.  The user needs to pay attention to the system's feedback and close RAM heavy processes BEFORE swap is used up.

On desktop systems with 8G and more, there is little need for more than 4G of swap unless you hibernate.  Hibernation has security problems, so I'll never us it, but I do use standby mode, which doesn't require a swap file larger than RAM. This is why I always use 4.1G of swap on all desktops.  Less isn't enough and more isn't helpful.

This is just my opinion.  Do what's right for you.

And for servers, the goal is to tune the amount of RAM provided so that no swap is needed. Most of my Linux servers have zero swap, but tuning them takes running with some swap for about 6 months to get performance monitoring data to KNOW how much RAM they actually require under all workloads. That's a completely different question.

---

### Post by jellicus on 2019-09-18
OK, I think I have the plan, to end up with the 2 logical partitions. Since I haven't actually installed Linux yet, there's no problem there. I don't use any sleep or standby since this is a fanless low power system there's very little power usage anyway, the TV gets turned off. There's no reason not to use an 4Gb swap, though it seems like I can spare 8 no problem.

---

### Post by jellicus on 2019-09-19
Installed. Though it's frozen twice now, which is discouraging.  Thanks all.

---

### Post by TheFu on 2019-09-19
> **jellicus said:**
> Installed. Though it's frozen twice now, which is discouraging.  Thanks all.

Linux machines should stay up and running for years without failing, unless it is tuned poorly or there is a hardware problem.  MS-Windows silently ignores many hardware problems, so when Linux is tried, they come to light and Linux gets blamed because "it worked in Windows."

Troubleshooting hardware issues in Linux isn't hard, but doing it is so very different than the way MSFT doesn't do it, it can be a challenge for someone without any Unix background.

Anyway, best to start a new thread for the freezing to get help on that.  There are a few common issues to be checked first. These forums have a number of threads helping others with the same symptoms, but usually the solution is different.

---

