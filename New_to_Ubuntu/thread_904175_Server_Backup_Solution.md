---
title: "Server Backup Solution?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by The Titan on 2008-08-29
I have a small server but it holds almost every single file that i don't want to lose.  I need to find a way to back up this system and have it automatically burn to disk (if this is possible)  It is Ubuntu Server 8.04 so it is a CLI system obviously.  I have tried bacula and it is just really confusing and the documentation for it really sucks when it comes to ubuntu.  I also was considering using cron but i dont know how to do that either so if anyone knows of a good tutorial for bacula cron, or some other alternative that would be great.   thanks in advance

---

### Post by jamelb on 2008-08-29
what I did was buy a cheap computer from. Retrobox.com and put a big hard drive. I than installed restore back up server. It's great and easy to use and is not only automatic but web based once installed. One tip I could only get it to use and internal drive. If you have any more questions pm me

---

### Post by The Titan on 2008-08-29
I cant really afford to buy even a cheap computer unfortunately.  Is there any way i could use this to back up locally?

Note:  Sorry i didn't PM, When i solve this i like to have the post for a reference.

---

### Post by indytim on 2008-08-29
Partimage may be an option.  It has a batch capability, although I've been unsuccessful at running it against a cron job.  You also have the ability to limit the size of the image files to accommodate either cd or dvd sizing.  I use it for my weekly partition backups and it offers quick recovery (3-4 minutes to rebuild a 10-15G partition).

Hope this is of some help.

IndyTim

---

