---
title: "Begginer with advanced questions :) RAID0/dual boot/Cloning"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by xcafeus on 2008-11-11
Hi guys,

I have installed 8.04 on RAID0 (fakeraid/nvidia) and upgraded to 8.10. Windows XP is the main OS (hd0,0) and Ubuntu was added later. Everything works fine in Ubuntu (for the 1st time) and I want to backup my Ubuntu installation and be able to restore it later on this raid0 setup. I have 3 partitions 0:Windows, 1: /, 2:swap. Is it possible to backup 1+2 and then incase of failure setup a new RAID0 with XP and restore the Ubuntu installation including grub?

I could use as more info as possible which is relevant to 8.10.

Thank you in advance,
xcafeus

---

### Post by xcafeus on 2008-11-12
this is similar to what Im looking for but must be applied to a raid0 system...

[http://www.faqs.org/docs/gazette/backup.html](http://www.faqs.org/docs/gazette/backup.html)

---

### Post by Kellemora on 2008-11-12
Hi XC

I'll warn ya ahead of time, I'm a grumpy Ole Man, hi hi........

Can the RAID and just mirror your drives!

You'll be glad you did!

Raid 0 nor Raid 1 give you any extra space, and only a false sense of security!

Data on Raid Drives are NOT RECOVERABLE without the EXACT controller that created them!  Do you have an identical spare laying around?

Data mirrored on two hard drives, unless the house burns down or you get hit with lighting, if one fails the other is still readable and can be mirrored back to a new drive.

Even Raid 5 will be obsolete by next year, hit its limits.

Just food for thought my friend!

TTUL
Gary

---

### Post by xcafeus on 2008-11-15
> **Kellemora said:**
> Hi XC

I'll warn ya ahead of time, I'm a grumpy Ole Man, hi hi........

Can the RAID and just mirror your drives!

You'll be glad you did!

Raid 0 nor Raid 1 give you any extra space, and only a false sense of security!

Data on Raid Drives are NOT RECOVERABLE without the EXACT controller that created them!  Do you have an identical spare laying around?

Data mirrored on two hard drives, unless the house burns down or you get hit with lighting, if one fails the other is still readable and can be mirrored back to a new drive.

Even Raid 5 will be obsolete by next year, hit its limits.

Just food for thought my friend!

TTUL
Gary


you re right regarding extra space and raid1 (isnt it mirroring in other words?) ...raid0 on the other hand gives you space (the space of all drives in the array) plus some extra speed but no data redundancy. Thats why I wanted to be able to back up my raid0 Ubuntu system and be able to easily restore it... I think I will be able to do this as soon as I master the use of a liveCD and the dmraid/chroot procedure.. unfortunately there seems to be no relative guide on the web (strange noone else is using raid0??) so I think Im on my own on this one..

thank you for your time and advice,
xc

---

