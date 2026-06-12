---
title: "Linux-Swap Partitions"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-14
I am/was running Xubuntu 11.04, and went to upgrade to the new 11.10. Unfortunately, I believe my computer overheated when I was gone, leaving the upgrade unfinished, and basically disabling me from using the currently installed Xubuntu. Luckily, I have a back-up disk, so I ran that, and am now preparing my partitions for installation in gParted. I noticed multiple little partitions called *Linux-Swap*.
[IMG]http://i.imgur.com/BVfIll.png[/IMG]

First of all, what is a *Linux Swap* partition?
Secondly, can I delete them?

---

### Post by wildmanne39 on 2011-10-14
Hi, it is used for putting your computer to sleep and for loading memory to the hard drive if you get low on memory.

It is best to have one that is 2 gigs in my opinion.
Thank you

---

### Post by wildmanne39 on 2011-10-14
Hi, One thing I should have mentioned, it is best to do a clean install, just back up your important data first.
Thank you

---

### Post by DaimyoKirby on 2011-10-15
**EDIT:** Oh. What if I don't really have any good place to put the files?

So you're saying I should delete the higher partition, and resize the last one to around 2 gigs?

---

### Post by wildmanne39 on 2011-10-15
Hi, yes you can delete the large swap but I do not think I would mess with resizing the 2.93, it is not that much larger then I suggested.

You will need to use a livecd and start gparted then turn of the swap, then you can delete it.

Here is a guide you should read before you change anything having to do with patitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
Thank you

---

### Post by DaimyoKirby on 2011-10-15
If I want to share files over a local(home) network, using an ethernet cable to connect to a router/modem, how would I set up a folder for sharing?

---

### Post by wildmanne39 on 2011-10-15
Hi, I do not know but that is off topic, you can start another thread on that issue, if I knew I would tell you though.
Thank you

---

### Post by mister_playboy on 2011-10-15
> **DaimyoKirby said:**
> If I want to share files over a local(home) network, using an ethernet cable to connect to a router/modem, how would I set up a folder for sharing?

Search the forums for topics about Samba and start learning. ;)

---

