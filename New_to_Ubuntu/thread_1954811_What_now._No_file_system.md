---
title: "What now. No file system"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by squrl on 2012-04-08
I am trying to load 12.04beta on a 500 gig drive that has Debian on it. 

The install goes fine till it wants to partition the drive then says no file system. I know it has Debian that runs. What else does it need. Even with a manual partition I cant find a way to get a /  or a boot partition. Someone please aim me in the right direction.

Thanks

---

### Post by Basher101 on 2012-04-08
use a live CD to boot up and select "Try Ubuntu" when prompted. 
Launch Gparted and partition the drive to your needs. Start the installer and set the mount points "/" and SWAP (if needed) manually. If you want/need SWAP create a partition with the same amount of space as the RAM (e.g. you have 2 GB ram = 2 GB SWAP).

---

