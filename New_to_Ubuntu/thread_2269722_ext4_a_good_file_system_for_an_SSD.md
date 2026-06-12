---
title: "ext4 a good file system for an SSD?"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-17
It is not necessary to defragment a system using the filesystem ext4 because it has ways it deals with fragmentation internally. "[FONT=Open Sans]If fragmentation does occur, the file system will attempt to move the files around to reduce fragmentation in normal use, without the need for a defragmentation utility." - [/FONT]http://www.howtogeek.com/115229/htg-explains-why-linux-doesnt-need-defragmenting/

Moving files to avoid fragmentation doesn't offer any performance increase for SSDs, though. Not only is it useless, it is detrimental to the life of the SSD because of unnecessary writing. Is there a way to disable this feature if using an SSD, or perhaps it is automatically disabled if it detects the drive as an SSD?

---

### Post by Vladlenin5000 on 2015-03-17
EXT4 is fine for SSDs and all current releases of all major Linux distros already take it in consideration and run a weekly cron job for FSTRIM. No other maintenance is needed and with any modern SSD you get a lifespan similar to the one of the old mechanical disks.

---

### Post by kerry_s on 2015-03-17
ubuntu does several things for ssd's under the hood, for example changing the elevator=deadline for performance instead of the standard cfq, fstrim already mentioned above, etc...

yes, you can go in & tweak things manually, for example some wish to have there fstrim done daily instead of weekly, just move it as root. you can add noatime, nodiratime, etc... it's up to you. there's no real need to go to extremes. best to install & use, simple right.

---

### Post by garycheng12 on 2015-03-17
Thanks for the answers.

---

