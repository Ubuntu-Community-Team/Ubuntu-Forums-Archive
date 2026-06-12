---
title: "reinstallation of 12.04 with SSD for boot, swap, and /, and separate HD for /home"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Old Jimma on 2013-02-05
Hi Community:

I may need to reinstall 12.04 and need a little guidance on how to reinstall it with my hardware configuration..

Currently, I have
[LIST]
[*]/boot, swap, and / on a 64GB SSD (/dev/sda), [*]/home on a separate HD (/dev/sdb) [/LIST]

When I reinstall, I'll use the Ubuntu installer, and tell it to:

[COLOR="Red"]specify partitions mannually (advanced).[/COLOR]

After doing that, I'll free all of the space on the ssd (/dev/sda), then:
[LIST]
[*]create a new partition table on [COLOR="Green"]**/dev/sda**[/COLOR],
[*]create a new EXT4 primary partition of 600MB for /boot, [*]create a logical partition for swap of 16MB,  and then [*]create a new logical EXT4 partition using the rest of the space on the SSD for / [/LIST]

My question is:at this point of the install, [LIST] [*]I want to specify my /home partition on [COLOR="Red"]**/dev/sdb**[/COLOR], but don't want to format it [*]and then  initiate the installation.
[/LIST]


Does this sequence of steps look correct?

Thanks,
Old Jimma

---

### Post by Calinou on 2013-02-05
You can uncheck "Format?" when selecting the /home partition.

---

### Post by Old Jimma on 2013-02-05
Thank you!

How do I specify /dev/sdb?

---

### Post by Paqman on 2013-02-05
> **Old Jimma said:**
> 
After doing that, I'll free all of the space on the ssd (/dev/sda), then:
[LIST]
[*]create a new partition table on [COLOR="Green"]**/dev/sda**[/COLOR],
[*]create a new EXT4 primary partition of 600MB for /boot, [*]create a logical partition for swap of 16MB,  and then [*]create a new logical EXT4 partition using the rest of the space on the SSD for / [/LIST]


Is there a particular reason you want to set your system up this way? You generally don't need /boot on a seperate partition, and 16MB is very small for a swap partition. If you actually mean 16GB then that's almost certainly bigger than you'll ever need. If it is only 16MB then I'd suggest simply creating a swap file instead of a very small partition.

The installer will show all drives attached to the machine, so you shouldn't have any problem telling it to use your existing /home partition on the second drive. I've installed that way many times myself without incident.

---

### Post by DuckHook on 2013-02-05
I recently bought a new machine for Christmas with an SSD/HDD combo, so had to go through exactly the same thought process as you. I had the advantage of a lot of advice from *oldfred*, so here were my considerations:

1. There are two primary concerns when setting up an SSD:
a) Write to it as little as needed so that it doesn't wear out from write fatigue,
b) Make sure the SSD is trimmed so that memory blocks are properly reclaimed from deleted files

2. The biggest Linux write processes are:
a) its propensity to record every file access, which creates a cascade of unnecessary writes.
b) temporary files, which are written to /tmp
c) log files, which are written to /var
d) swap especially if you don't have a lot of system memory
e) depending on your usage, data written to /home

3. A further consideration is ext3/4 journaling which is quite write-intensive. However, disabling journaling just to save on SSD wear and tear struck me as rather a poor trade. I'd much rather have the safety and security of journaling than an extra year or two of disk, so I left journaling on.

You solve 1b and 2a with two simple adjustments to fstab for any filesystem on the SSD. These are: noatime and discard. The first option tells Linux to not record file access times. The second tells the system to turn on trimming. Of course, the HDD doesn't need these settings. I then solved 2b, c, d & e by making separate partitions for each of those directories on my HDD. I wanted hibernation, so I carved off enough for a swap equal to my RAM in GiB  plus 1GB for margin of safety. /tmp and /var don't need to be large, but given the size of HDDs these days I left generous partitions for them of 2GB and 4GB respectively. The rest went to /home.

The system now boots up like greased lightning and accesses the SDD only for apps and system resources and even then, mostly for reads. Writes to the SSD are very low. You may wish to set yours up differently, but this works very well for me.

BTW, if you are installing to a UEFI partition, your /boot may actually be residing on the UEFI partition which will likely be on your SSD. You don't need yet another separate /boot. All of my disks were partitioned with GPT, not MBR, so the number of partitions were not limited to 4. However, the above scheme would still fit inside the old MBR constraints.

---

### Post by Old Jimma on 2013-02-08
Thanks Duck!

... also, I meant 16Gb!

---

### Post by Paqman on 2013-02-10
> **Old Jimma said:**
> Thanks Duck!

... also, I meant 16Gb!

The only reason to have a 16GB swap is if you have 16GB of RAM and need to use hibernation. If you don't need to use hibernation and you have over about 2-3GB of RAM I'd advise having a very small swap (0.5-1GB) or no swap at all.

---

### Post by DuckHook on 2013-02-10
I have enough RAM that I don't really need a swap. However, it's the only way to allow hibernation. And HDD space is so cheap these days that 16GB is easy to give away. I resolved the matter by setting my swappiness to 0. Instructions [here]("https://help.ubuntu.com/community/SwapFaq").

Swap is one of these topics which are discussed endlessly and for which there really isn't a right or wrong answer. It all depends on each user circumstance and usage-case. @Paqman provides a very solid rationale for doing away with it altogether on high-RAM systems without hibernation. Hibernation itself is an option that is no longer default in Ubuntu and for which special steps are necessary to enable. However, if your system is less than 4GB, I would certainly recommend that you keep swap.

BTW, a further tweak for SSD is to set the io scheduler to "deadline". This won't make a really big difference, but what's the point in buying a SSD if we don't try to squeeze as much extra performance from it as possible?

1. create file:```
sudo nano /etc/udev/rules.d/95-uuid-ioscheduler.rules
```2. add line:```
ENV{ID_FS_UUID}=="xx", ATTR{../queue/scheduler}="deadline"
``` ...where xx is UUID of SSD(keep the quote marks).

3. Reboot. Check for proper change in scheduler with:```
cat /sys/block/sdx/queue/scheduler
``` ...where x is device letter of SSD disk (i.e. sda).

For explanation and comparison of schedulers, see [this]("http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance").

---

### Post by Paqman on 2013-02-10
> **DuckHook said:**
>  HDD space is so cheap these days that 16GB is easy to give away.

True.

In fact when it comes to partitioning in general there's no need to fret over getting it perfect. You can always change it later.

>  I resolved the matter by setting my swappiness to 0. Instructions [here]("https://help.ubuntu.com/community/SwapFaq").

I do this too, and rarely see any swap activity.

---

