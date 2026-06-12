---
title: "Large SMB file transfers causing system hangs"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by BadAstronaut on 2008-04-28
I installed Ubuntu (alternate install - no desktop) on a surplus PowerEdge 300 last month, then updated to Hardy this week.  I'm new to Linux, so I'm not even sure what logs or diagnostics might explain my situation:

System is booting off of a 20GB RAID 1 mirror with no problems.  Samba installed & configured with SWAT, and looks good from my XP and Win2K machines.  Three 500GB SATA drives (off a Promise TX4 PCI controller) in RAID 5 configuration for data storage, partitioned via LVM.

Nifty.  However, when I attempt to copy a large file (a few GB or more) from XP to the server, the system seems to hang -- SSH session goes down, console unresponsive.  The transfer does appear to complete successfully, though.

(Before I learned about REISUB SysRq, I had no choice to power down and then endure a lengthy RAID resync.)

I'd love to know what I should be looking at to solve this problem.  Thanks for any advice you can offer.

PS: I had the same experience a little while ago after copying over a 5GB file (not that I expected it had magically fixed itself or anything.)  But this time I was patient, and waited an hour before trying to SSH back into the box.  It was up & running & stable as far as I can tell.  Where can I look to see what it was doing during the "downtime?"

---

### Post by BadAstronaut on 2008-04-29
Ah, I *knew* I should've posted before the Hardy release soaked up everyone's attention...

:rolleyes:  I'll keep at it.  Must be something foolish I've done, or others would be having the same problem, eh?

---

### Post by BadAstronaut on 2008-05-01
Well, I'm about out of ideas.

Based on tips here, Launchpad, and elsewhere, I've made modifications to my smb.conf, disabled IPv6 support, attempted to disable (unsupported) checksumming on my ethernet card, and have kept a CD in the CD-ROM drive.

It **does** appear that plenty of other people have the same sort of problem (and have been for years) -- but either their root cause is slightly different or they are still searching for a solution, too.

All in all, a somewhat disappointing introduction to Ubuntu.  I may be looking at Openfiler or FreeNAS as a fallback option.

---

### Post by Gertjan on 2008-06-22
Hi! I experienced the same problem, but not with Samba. I have build a Linux system with 4 400GB SATA drives in software RAID 5, and Linux itself on an USB stick. Recently I reinstalled Linux (Debian 4.0, etch) on the USB stick, and then the problems started.

When unpacking movies (legally downloaded since I own the original on DVD ;-)) the system would freeze after 1.5 GB or so. I could still login to the system by SSH, but a lot of commands that would do anything with the disks (shutdown, sync, dd) would indefinitely block.

Searching for a solution I came across your posts, and this remark made me remember:

> **BadAstronaut said:**
> 
After wading through a bunch of Google results, I'm intrigued by the possibility that increasing /sys/block/md2/md/stripe_cache_size to 1024 (or greater) might be a step in the right direction, but I'm not sure how to do this.  (And I suppose this is now the wrong forum category to be asking ... perhaps I should take it to Server Platforms instead?)

**Update:** Taking a wild guess, I added my stripe_cache_size value override to rc.local and rebooted.  First test (with an 8.5GB file) completed successfully, but the second didn't complete & hung the system again.


On the previous install I used an optimization script, that included raising the stripe_cache_size. I forgot to apply those optimizations in this new install. After applying this script everything works again as it should.

This is my script, composed from tips in these threads: [http://www.mail-archive.com/linux-raid@vger.kernel.org/msg10314.html](http://www.mail-archive.com/linux-raid@vger.kernel.org/msg10314.html). 

```

echo 1024 > /sys/block/sda/queue/max_sectors_kb
echo 1024 > /sys/block/sdb/queue/max_sectors_kb
echo 1024 > /sys/block/sdc/queue/max_sectors_kb
echo 1024 > /sys/block/sdd/queue/max_sectors_kb
blockdev --setra 65536 /dev/sda
blockdev --setra 65536 /dev/sdb
blockdev --setra 65536 /dev/sdc
blockdev --setra 65536 /dev/sdd
blockdev --setra 65536 /dev/md0
echo 16384  > /sys/block/md0/md/stripe_cache_size

```

---

### Post by BadAstronaut on 2008-06-22
The script definitely had a positive impact!  After implementing it (modified to suit my configuration, of course) I was able to copy over almost 30GB of data before the system went catatonic again.

Ironically, just yesterday [I posted a final cry for help over in the Server section]("http://ubuntuforums.org/showthread.php?t=836713"), stating that I was about to give up.  Now I have hope again.

One of the things I tried in hopes of eliminating this problem was reformat my XFS volume as EXT3.  But I see that the thread you referenced was about RAID 5 + XFS ... so perhaps once I reformat back I'll see even better results.

---

### Post by bihe on 2008-10-26
Hi there,

sounds strangely similar to [http://ubuntuforums.org/showthread.php?t=913118]("http://ubuntuforums.org/showthread.php?t=913118")

This helped: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094/comments/112]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094/comments/112")

---

