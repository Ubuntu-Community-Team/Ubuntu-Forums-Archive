---
title: "RAID0 - A few questions"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by hobx on 2008-06-11
Okay, after a few days of playing around, I finally got my Raid0 configuration setup and mounted on my desktop. I now have a few questions I can't find the answer for online.

1) fdisk output shows /dev/md0 doesn't containt a valid partion table - I think this is just because fdisk and gparted can't read RAID paritions correctly? Is this right? Can I just leave this?

2) Lost + Found and disk usage. If I right click the raid on my desktop and look at properties, it shows that 30gb is used. I haven't added anything to the disk yet and when I looko inside, the only folder is lost+found. My understanding of RAID0 is that there should be minimal or no overhead. What is taking up 30gb?

3) Permissions, at the moment, I can only write by elevating to root. Is this correct, if I change the permissions to my account will everything be okay?

I'm currently at work so can't give any output until this evening (about eight hours from now) so I'm just looking for general thoughts?

I'm using Hardy, and each drive is a 320gb seagate drive. I set up the raid array using mdadm and formatting the raid with ex3 using mkfs. The drives are connected to a ITE8212 which is acting as a straight ide bus.

Thanks in advance

---

