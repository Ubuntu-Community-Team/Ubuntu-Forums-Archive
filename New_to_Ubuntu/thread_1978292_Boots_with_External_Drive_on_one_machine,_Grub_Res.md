---
title: "Boots with External Drive on one machine, Grub Rescue on another"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by rickygarg on 2012-05-11
Hi, 

I installed ubuntu 12.04 on my vaio sr13gn and despite repeated attempts and using boot-repair, the grub rescue prompt remains. Since I am not using any internal drive, I am sure that my bios is booting into my external drive.

This external drive installation boots Ubuntu just fine on my other machine - vaio sz series despite the fact that I installed Ubuntu on SR 13 GN laptop.

So I am assuming that the BIOS on my SR 13 is having issues recognizing the sdb6 partition where boot files are located even though it is able to recognize sdb where grub is installed.

Any solution will be much appreciated. I tried searching for few hours before posting this but couldn't find anybody with the same issue.

---

### Post by oldfred on 2012-05-11
If it is an older computer, then it may have the 137GB BIOS boot limit. 

Or it could be BIOS settings for IDE only that emulates the old limit. 

I might look at BIOS settings if a newer (last 6 yrs) and see what you have. Each system uses different names but you want large, LBA, or the newest AHCI, but XP needs AHCI drivers installed when you install XP, With Windows 7 you can install the AHCI drivers before rebooting and changing BIOS.

Some other odd settings like fastboot or quickboot can make a different also, Turn those off.

---

### Post by rickygarg on 2012-05-11
> **oldfred said:**
> If it is an older computer, then it may have the 137GB BIOS boot limit. 

Or it could be BIOS settings for IDE only that emulates the old limit. 


You hit the bulls eye here I think. I will repartition such that my boot files are before 137 GB. Still, for the sake of discussion, could you elaborate on the second point? How could I check that?

---

### Post by oldfred on 2012-05-11
How old is computer?

Everyone's BIOS seems to be different and I believe BIOS settings make a difference, but it can be hard to track down. Some have just experimented and fixed it, other give up, and some just reinstall.

You can either have a separate /boot or install with / (root) fully in the first 137GB and /home or other data partitions beyond the 137GB limit. It is just booting that is the issue. Often older systems with new larger hard drives.

---

### Post by rickygarg on 2012-05-11
Actually my other SZ (on which it was running good) is older ! 

Now messaging from my new 12.04 installation. I shrinked my windows partition and ensure that the partition on which boot exists comes withing 137 GB. Thanks so much!

---

### Post by oldfred on 2012-05-11
Glad that worked. :)

---

