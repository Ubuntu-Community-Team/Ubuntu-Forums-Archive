---
title: "Want to buy a portable SSD to run Ubuntu on - Need advice"
date: 2020-08-06
forum: New to Ubuntu
---

### Post by sezza on 2020-08-06
Hi all

I need some advice, I would like to buy a Portable SSD to install Ubuntu MATE on..

My computer only has USB 3.1 Type A connectors, I cant decide between the following two:

Sandisk Extreme Portable SSD - [https://shop.westerndigital.com/products/portable-drives/sandisk-extreme-usb-3-1-ssd#SDSSDE60-250G-G25](https://shop.westerndigital.com/products/portable-drives/sandisk-extreme-usb-3-1-ssd#SDSSDE60-250G-G25)
Sandisk Extreme Pro Portable SSD - [https://shop.westerndigital.com/products/portable-drives/sandisk-extreme-pro-usb-3-1-ssd#SDSSDE80-500G-A25](https://shop.westerndigital.com/products/portable-drives/sandisk-extreme-pro-usb-3-1-ssd#SDSSDE80-500G-A25)'

The portable pro can get speeds up to 550 mb/s where as the other 1000mb/s. However, what I want to know is:
[LIST]
[*]Which is enough to run UBUNTU Mate comfortably off the SSD? 
[*]Considering I only have USB 3.1 is it worth getting the more expensive option? My other PC is even older, an older ThinkPad X1 Carbon i5 5th gen... I dont even know if its USB 3, I think it does but not necessarily 3.1 
[*]Would the more expensive option be better for future-proofing or would it be easier to just buy a new one when I eventually get a new PC (which is a few years away still). 
[/LIST]

Advice would be appreciated, many thanks!

---

### Post by TheFu on 2020-08-06
Any SSD is more than fast enough to run any Ubuntu comfortably. Any performance over 100 MB/s is great for the OS.  Beyond that is gravy and you'll only notice at boot time, if then.

I wouldn't get SanDisk. I'd get Samsung if endurance matters. Be certain to check the specific model for issues with Linux systems.  [https://forums.sandisk.com/t/linux-wont-detect-my-ssd/74643](https://forums.sandisk.com/t/linux-wont-detect-my-ssd/74643)

Pretty much any SSD using any USB3 port should work great - much faster than any flash drive or spinning disk as to not matter at all.  I saw a 240G PNY SSD for $19 a few days ago. Think the normal price is $25.  Many people lose their portable storage. If you are one of those people who can't find a thumb-drive from 2010, perhaps stay on the cheap side.  I just picked up (in my hand) a 128MB thumbdrive from 2007 given by a vendor. I've been putting cheap, excess, m.2 SSDs into a $9 USB3-c enclosure for years. Basically, a new PC comes with a 64G or 128G SSD and I replace it with a 500G one. Those old SSDs are fine and just need a home to be used - enclosure.
Found that deal: PNY CS900 SSD (**120GB $14.46**, 240GB $22.46) Staples YMMV.

For any external SSD, I don't see the point in spending for high speed. You won't notice the difference unless moving huge files back and forth daily. Who does that?  And if you do, the SSD will wear out much faster.  I've done something like that with video files and expensive thumb-usb3 storage. Just over a year later and the name-brand storage was worn out. I use a $9 WD 250G (bought used at Microcenter) spinning HDD for that purpose now.

"up to 550 mbps" ... means that under ideal, labortory conditions, someone, never you, might see that speed, once over 1,000,000 attempts.  The rest of the time, expect more like 350 mbps.  Considing that USB3 bus supports 5Gbps .... it just doesn't matter.  

And we need to be VERY, VERY, clear about units here.  "mb/s" is "megabits per second."  The specs say MB/s "megabytes" .... which is very different. 8x more.  mb = megabits.  MB = megabytes.  Performance for networking is always mbps.

Only buy the storage you need today, today. All storage is going to fail. Our goal is for it to fail AFTER we are done using it in critical situations.  Additionally, all storage will get cheaper over time, just like CPU performance goes up over time. Forget "future proofing." In two years, the new storage will be all USB4 with 40 Gbps speeds (10x fast than 500 MBps). [https://en.wikipedia.org/wiki/USB4](https://en.wikipedia.org/wiki/USB4)  I'm completely serious.  You'll be able to get the high-end stuff today for $15.

IMHO.

---

### Post by pbear42 on 2020-08-06
Side note.  Perhaps you already know this, but be aware there's a bug in the Ubuntu installer which will bollix your internal drive's boot loader when installing to USB drive in UEFI.  There are several workarounds.  The bollix isn't all *that* difficult to fix, but better to avoid the problem in the first place.

On the bright side, I have several multi-boot USB hard drives.  They're really cool.

---

### Post by sezza on 2020-08-07
> **TheFu said:**
> 

Pretty much any SSD using any USB3 port should work great - much faster than any flash drive or spinning disk as to not matter at all.  I saw a 240G PNY SSD for $19 a few days ago. Think the normal price is $25.  Many people lose their portable storage. If you are one of those people who can't find a thumb-drive from 2010, perhaps stay on the cheap side.  I just picked up (in my hand) a 128MB thumbdrive from 2007 given by a vendor. I've been putting cheap, excess, m.2 SSDs into a $9 USB3-c enclosure for years. Basically, a new PC comes with a 64G or 128G SSD and I replace it with a 500G one. Those old SSDs are fine and just need a home to be used - enclosure.
Found that deal: PNY CS900 SSD (**120GB $14.46**, 240GB $22.46) Staples YMMV.

For any external SSD, I don't see the point in spending for high speed. You won't notice the difference unless moving huge files back and forth daily. Who does that?  And if you do, the SSD will wear out much faster.  I've done something like that with video files and expensive thumb-usb3 storage. Just over a year later and the name-brand storage was worn out. I use a $9 WD 250G (bought used at Microcenter) spinning HDD for that purpose now.

"up to 550 mbps" ... means that under ideal, labortory conditions, someone, never you, might see that speed, once over 1,000,000 attempts.  The rest of the time, expect more like 350 mbps.  Considing that USB3 bus supports 5Gbps .... it just doesn't matter.  


IMHO.

Thank you for the advice.

Question, so if "up to 550mbps" means the rest of the time I Get 350 mbps, would a SSD that has up to "1000mbps" mean I only get "750mbps" most of the time.. or it would still be much much lower as in 350 mbps?

---

### Post by sezza on 2020-08-07
> **pbear42 said:**
> Side note.  Perhaps you already know this, but be aware there's a bug in the Ubuntu installer which will bollix your internal drive's boot loader when installing to USB drive in UEFI.  There are several workarounds.  The bollix isn't all *that* difficult to fix, but better to avoid the problem in the first place.

On the bright side, I have several multi-boot USB hard drives.  They're really cool.

Hi, no I didn't know, thank you for telling me though :) will do a bit of research into this before installing :)

---

### Post by sudodus on 2020-08-07
There is advice how to install Ubuntu into a USB drive at [this link](https://askubuntu.com/questions/1263746/ubuntu-doesnt-boot-from-usb-stick/1263749#1263749) and the three links from it.

---

### Post by TheFu on 2020-08-07
> **sezza said:**
> Thank you for the advice.

Question, so if "up to 550mbps" means the rest of the time I Get 350 mbps, would a SSD that has up to "1000mbps" mean I only get "750mbps" most of the time.. or it would still be much much lower as in 350 mbps?

mbps and MBps aren't the same. The most important part of my reply out was removed!

As for performance, the workload will determine that.  Sometimes is will be 10 - 80 Kbps and sometimes it will be higher. Depends completely on the workload.  USB storage protocol isn't the best for a running OS. I've seen queuing problems over USB connections. Use SATA or eSATA when possible.

Some real-world transfers:
```
  2,922,988,208 100%   80.62MB/s    0:00:34 (xfr#1, ir-chk=1002/3916)
          9,392 100%    9.30kB/s    0:00:00 (xfr#2, ir-chk=1001/3916)
      9,880,928 100%   57.11MB/s    0:00:00 (xfr#2, to-chk=38/11933)
             69 100%    0.41kB/s    0:00:00 (xfr#3, to-chk=36/11933)
              5 100%    0.03kB/s    0:00:00 (xfr#4, to-chk=35/11933)
             62 100%    0.35kB/s    0:00:00 (xfr#5, to-chk=33/11933)

```
Those are from an **rsync** of some files between 2 disks this morning.  The fact that the SOURCE is connected with a 6 Gbps SATA connection and the TARGET is a 5 Gbps USB3 connection doesn't matter because both are spinning disks and nowhere near the theoretical max for the bus.  Using SSDs gets closer and really FAST SSDs can exceed USB3.1 speeds.  Enterprise NVMe can get to 32 Gbps (8 GBps) - that's an x4 PCIe connection almost always.

The 1st xfer above has a fast enterprise HDD as the source. The others have a "NAS" HDD as the source.  Notice how the larger files have better performance?  That is common, since accessing small files has more overhead.  Running programs is more like accessing lots of small files.  You are worried about performance that just doesn't matter in the real world.  Plus, the system where these xfers were running has enough RAM to buffer the files into RAM, so the write speed really didn't enter into those numbers.  Those are read-limited.
80 MB/s = 640 Mb/s which is nowhere near even SATA-I bandwidth, so USB3 wouldn't be an issue either.

Run the numbers for your proposed hardware ... but for running an OS, it likely will never matter.

---

