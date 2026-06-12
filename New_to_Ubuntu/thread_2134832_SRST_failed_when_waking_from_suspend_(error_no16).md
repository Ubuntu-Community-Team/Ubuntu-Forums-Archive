---
title: "SRST failed when waking from suspend (error no16)"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by samjhooker on 2013-04-12
have dual booted my Lenovo U410 Ultrabook with Ubuntu and it has ben running great (far better than Windows 8).
However, everytime i wake my laptop from suspend (open the lid) it says this messege.

ata1: SRST failed (errno=-16)
ata1: SRST failed (errno=-16)
ata1: SRST failed (errno=-16)
ata1: SRST failed (errno=-16)
ata1: Reset failed, giving up (errno=-16)

It says this for about 40 seconds before the lockscreen pops up. I have read previous forum posts and have learnt it may have something to do with the HDD or SSD but nothing good has worked to stop it from poping up. The only thing that has worked has been to disable suspend altogether. This makes resume from suspend instant but it constantly eats my battery.

Any help to fix this is highly appreciated,
Thank you

---

### Post by samjhooker on 2013-04-14
Anyone?

---

### Post by athletesrun on 2013-05-08
> **samjhooker said:**
> have dual booted my Lenovo U410 Ultrabook with Ubuntu and it has ben running great (far better than Windows 8).
However, everytime i wake my laptop from suspend (open the lid) it says this messege.

ata1: SRST failed (errno=-16)
ata1: SRST failed (errno=-16)
ata1: SRST failed (errno=-16)
ata1: SRST failed (errno=-16)
ata1: Reset failed, giving up (errno=-16)

It says this for about 40 seconds before the lockscreen pops up. I have read previous forum posts and have learnt it may have something to do with the HDD or SSD but nothing good has worked to stop it from poping up. The only thing that has worked has been to disable suspend altogether. This makes resume from suspend instant but it constantly eats my battery.

Any help to fix this is highly appreciated,
Thank you

I have this same problem.  Fortunately, the error only lasts about 8 seconds and then goes to the normal lockscreen.   I havent been able to find anything to fix this.  I'm using a dell latitude d630

---

### Post by oldfred on 2013-05-08
That is Windows caching for UltraBooks. You may want to discuss in a Windows or Intel forum.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Some that are primarily Linux users just install / (root) to the SSD and leave the SRT off.

---

### Post by äxl on 2013-05-12
Thanks, oldfred, but no. It's SR**S**T not SRT. Still Intel's got some PDFs which pin this problem to Soft/-ware/Stream/System ReSeT.
I have this problem since LMDE UP4 but it only lasts four seconds.
```

May 12 13:58:57 homepc kernel: [    1.511489] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
...
May 12 13:58:57 homepc kernel: [    7.020018] ata3: link is slow to respond, please be patient (ready=0)
...
May 12 13:58:57 homepc kernel: [   11.556013] ata3: SRST failed (errno=-16)
May 12 13:58:57 homepc kernel: [   12.024034] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 12 13:58:57 homepc kernel: [   12.032255] ata3.00: ATA-8: Patriot Torqx 2 32GB SSD, S5FAM007, max UDMA/100
May 12 13:58:57 homepc kernel: [   12.032298] ata3.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 0/32)
May 12 13:58:57 homepc kernel: [   12.048251] ata3.00: configured for UDMA/100

```
Strangely enough it worked some weeks in Squeeze. Fortunately the system isn't frozen like in Mint.
Then I had a problem with a HDD (bad blocks) and since something's fishy with the device order. Seems this only occurs when external devices are loaded first.

This was normal:
```

May 10 22:23:24 homepc kernel: [    1.269444] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
...
May 10 22:23:24 homepc kernel: [    1.736033] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 10 22:23:24 homepc kernel: [    1.744254] ata3.00: ATA-8: Patriot Torqx 2 32GB SSD, S5FAM007, max UDMA/100
May 10 22:23:24 homepc kernel: [    1.744295] ata3.00: 62533296 sectors, multi 1: LBA48 NCQ (depth 0/32)
May 10 22:23:24 homepc kernel: [    1.760258] ata3.00: configured for UDMA/100

```

Changing boot order?!?
[https://bbs.archlinux.org/viewtopic.php?pid=1012038](https://bbs.archlinux.org/viewtopic.php?pid=1012038)

I hope this doesn't lead to more problems:
[http://www.ocztechnologyforum.com/forum/showthread.php?98525](http://www.ocztechnologyforum.com/forum/showthread.php?98525) [limiting SATA link speed to 1.5Gbps]
[http://www.computerbase.de/forum/showthread.php?t=1063281](http://www.computerbase.de/forum/showthread.php?t=1063281) [German but look at the log – reset failed, giving up – ata1.00: disabled]

---

### Post by oldfred on 2013-05-12
Is it still related to the SSD that is for Windows 8 and the Intel SRT?

The UEFI/BIOS has to report that SSD device and as a RAID/SRT then Ubuntu may have issues with it?

This user converted SSD to flashcache.
  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

### Post by äxl on 2013-05-12
Oh, I guess you're right, oldfred.

My problem is also only at start not when suspending to RAM. Though I don't really understand the need for S2R with Linux and a SSD. Or flashcache in that case ...
I checked the kern.logs some more and it seems it's really got something to do with the booting order.

---

### Post by äxl on 2013-05-17
Problem solved itself. Didn't change any BIOS settings or cabling but during these days my USB mem stick was automatically mounted which wasn't working before and isn't now ...

But back to your problem samjhooker: Could you give us some logs, like /var/log/pm-suspend.log or /var/log/syslog ...

---

