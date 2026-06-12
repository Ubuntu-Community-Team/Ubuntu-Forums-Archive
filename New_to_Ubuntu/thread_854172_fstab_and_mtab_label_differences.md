---
title: "fstab and mtab label differences"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by cy218 on 2008-07-09
Please point me to a thread if this has already been explained but I didn't even know where to start!

I've just upgraded to Hardy which was very easy (for which I'm grateful). Since then I've noticed that my drive/partition device names are now sda for my internal drive and sdb for my external drive. These labels are used when I use fdisk, df -h, look in /etc/mtab and system monitor.

However, when I look in /etc/fstab the internal drive is still labelled hda, which is what it was before I reinstalled.

A number of questions please:

1. Why??
2. Is this a problem (potential problems for upgrade etc)?
3. What do I do about it?

Again, if this has been covered ad nauseum then I apologise, just point me towards a link.

Many thanks

Cy

---

### Post by ibuclaw on 2008-07-09
There have been alot of changes since Ubuntu 6.06, and it seems understandable that a few settings would be left behind in the upgrade.

Have you rebooted your PC yet?

If you have, and they are still the same. I shouldn't worry too much about it/I can't think of any problems being caused if the mtab were displaying the wrong info. If all appears to mount and function fine. We can call this a close shave.
Afterall, in reality there is no difference between **h** and **s**, just one is the old way of referring to hard-drives, and the other is the new. (although, if your fstab file would refer to them as **hda**, then that would cause huge problems!).

If it does bother you with a huge passion, you could always do a clean install of Hardy. But make sure to back-up everything first.

Regards
Iain

---

### Post by cy218 on 2008-07-09
Thanks Iain

The install has stood up fine for a couple of weeks, so no problem there.

I backed up my /home partition then did a clean install from a 7.10 disk, then immediately upgraded to Hardy. After that I dragged whatever I wanted from my backed up /home to my new /home being as specific as possible so as not to overwrite useful stuff from the new install.

I'm not aware of anything I did that would provide a hang over from my old Dapper install. Although I don't know much so I could very well be wrong!

I suppose it's not that important but I still wonder why?

Thanks again for your help.

Cy

---

### Post by booja on 2008-10-07
> **tinivole said:**
> 
(although, if your fstab file would refer to them as **hda**, then that would cause huge problems!).

One of my HDs (sda1) is disappearing sometimes when I login or maybe it already disappeared before but I only notice when logging in. Could this be the cause?

fstab
# /dev/hda1 -- converted during upgrade to edgy
UUID=c42a5fc7-2398-483f-8975-16bfddd446c0 /mnt/hda1 ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=5defc5df-95e3-4841-8b9b-b1c45847face /mnt/hdb1 ext3 defaults 0 2

mtab
/dev/sda1 /mnt/hda1 ext3 rw 0 0
/dev/sdb1 /mnt/hdb1 ext3 rw 0 0

When I run /etc/init.d/mountall.sh it comes back though.

---

