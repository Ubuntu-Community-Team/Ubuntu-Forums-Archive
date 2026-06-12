---
title: "HOWTO: Set up RAID 0 parititions so GRUB works"
date: 2006-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by jadfw007 on 2006-08-16
Like others have, I got a really nasty error on grub-install after setting up RAID 0 partitions. I eventually figured out that GRUB needs a bootable, *non-RAID* partition on one of the drives. Here's what my partitions looked like just before I finally succeeded in installing GRUB (and subsequently succeeded booting).

HDD 1:
[LIST]
[*]Partition 1: .5 GB, primary, "/boot", ext3, bootable
[*]Partition 2: 3.5 GB, logical, swap
[*]Partition 3: remaining space, logical, RAID device
[/LIST]

HDD 2:
[LIST]
[*]Partition 1: 4 GB, logical, swap
[*]Partition 3: remaining space, logical, RAID device
[/LIST]

Software RAID:
[LIST]
[*]Partition 1: all available space, "/", ext3
[/LIST]

This is not very detailed, and my wording might not be 100% accurate. But it's 430a, so hopefully you get the idea b/c this is all you're getting :twisted: 

HTH!

---

