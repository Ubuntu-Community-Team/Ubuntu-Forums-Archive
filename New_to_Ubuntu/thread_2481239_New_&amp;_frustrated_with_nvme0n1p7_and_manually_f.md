---
title: "New &amp; frustrated with nvme0n1p7 and manually fsdk"
date: 2022-11-23
forum: New to Ubuntu
---

### Post by redexplor on 2022-11-23
Hi!

First of all, I’m sorry if this is something very basic and I’m stuck in nonsense. 
After an amazing week with Ubuntu in my laptop (with a dual boot with windows 11) yesterday I got into windows for a moment and when I went back to Ubuntu it gave me the following error: 

UNEXPECTED INCONSISTENCY: RUN fsck
MANUALLY
fsck exited with status code 4
The root filesystem on /dev/nvme0n1p7

I read a bunch of post and videos about this and finally - after try a lot of options - I runned fsck /dev/nvme0n1p7 and start an never ending process pressing y. 
I also tried to run Ubuntu from the installation USB with sudo and same option but with same result. 

I have no problem to re-made the installation from 0. But I really want to understand what’s happening to learn something and - over all - to not repeat it in the future :) 

Thank you very much in advance!

---

### Post by yancek on 2022-11-23
Use the y option in the command so that you do not have to enter y constantly.  Also unmount the partition before running it.

>  fsck -y /dev/nvme0n1p7

The link below gives some explanation on using fsck including options you can use (at bottom of the page).  If that is not sufficient for you, doing an online search for using fsck on Linux should provide a number of sites.

[https://phoenixnap.com/kb/fsck-command-linux](https://phoenixnap.com/kb/fsck-command-linux)

---

### Post by tea for one on 2022-11-23
> **redexplor said:**
> But I really want to understand what&#8217;s happening to learn something and - over all - to not repeat it in the future
Assuming that /dev/nvme0n1p7 is your Ubuntu system partition, it is possible that you had to run fsck because the system did not shut down cleanly.
Did you notice anything unusual when you previously closed Ubuntu?

---

