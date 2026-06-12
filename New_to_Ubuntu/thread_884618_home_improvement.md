---
title: "home improvement"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-08-09
Hi,

A little help please.

I recently reinstalled Ubuntu due to problems described [here]("http://ubuntuforums.org/showthread.php?t=878690"). Before doing that, I partitioned my drive and copied the /home folder over according to instructions found on [psychocats]("http://www.psychocats.net/ubuntu/separatehome").

After that, I am left with two partitions on my sata drive, and one on my IDE. (Check my signature for spec).

When installing, I went for a manual partition and, thinking I was smart, chose the mount points for each for the root "/" (sdb1) and the home directory "/home" (sdb3)

The installation went ahead and seemed to be successful. However when I rebooted I got a tonne of error messages and I couldn't log in. 

So I just reinstalled - this time again choosing to install on sdb1, but leaving out details of where home should be mounted. This time it worked fine.

However, I have now got a second partition with all my documents and settings in a home folder not being used while the home folder on sdb1 is practically empty. 

So I need to know, how to tell Ubuntu to use sdb3 for the home partition, rather than sdb1. By the way, I have googled this to death but can't seem to find a fix that exactly applies to my problem. 

Cheers,

James.

---

### Post by Steveway on 2008-08-09
I have to do this, sorry for being OT:

"I don't think so Tim."

(For your problem: Look into manuals about Fstab, that is the place you need to take a look.)

---

### Post by Jimmy9pints on 2008-08-09
> **Steveway said:**
> I have to do this, sorry for being OT:

"I don't think so Tim."

(For your problem: Look into manuals about Fstab, that is the place you need to take a look.)

I had to google that then. [If anyone else is wondering]("http://en.wikipedia.org/wiki/Home_Improvement")

---

### Post by Jimmy9pints on 2008-08-09
read man mount and man fstab.

Is there anything simpler out there, I am totally lost

---

### Post by sisco311 on 2008-08-09
fstab line:
> UUID=<**insert uuid here**> /home ext3 defaults 0 2to list the uuid:
```
sudo blkid /dev/sdb3
```to edit the file:
```
gksu gedit /etc/fstab
```

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by lukjad on 2008-08-09
I love that show! Thanks for the flashback.

---

