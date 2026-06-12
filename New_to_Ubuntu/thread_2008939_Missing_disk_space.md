---
title: "Missing disk space"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by anbelo on 2012-06-23
Hello everybody,

(and sorry in advance for my English).

I'm using Ubuntu 11.04. Today after a power failure the system performed the usual disk comprobations (wich took a very long time) and when it finally started I found that my Incoming folder (for aMule) was empty. But I wouldn't post here about that: the thing is df -h shows that the size of my /home partition (which contains the Incoming folder) has decreased by almost 80 Gb (the **total** space, not the used one).

I ran fsck in single user mode for the /home partition after unmounting it and it shows 0 bad blocks.

I haven't noticed any more missing files or problems by now, but would like to know what has happened, and where those 80 Gb of disk space have gone!

Thank you very much.

---

### Post by Frogs Hair on 2012-06-23
Hello and Welcome

Try rebooting and check again . I had a similar incident and when the power came back on I started the computer as you did. Ubuntu did not report the correct disk space until rebooting again.

---

### Post by audiomick on 2012-06-23
> **anbelo said:**
> 
(and sorry in advance for my English)..


Your English is better than some English speakers who post here. ;)

---

### Post by anbelo on 2012-06-24
Thank you for your reply, Frogs Hair (and thank you too, audiomick :p). I have rebooted several times since then, and the problem remains. You can see it in the following screen captures:

df -h shows 745G for /home

[IMG]http://imageshack.us/photo/my-images/696/dfhc.png[/IMG][IMG]http://img696.imageshack.us/img696/7066/dfhc.png[/IMG]

While Disk Utility still shows the original 812 G:

[IMG]http://img88.imageshack.us/img88/8022/diskutil.png[/IMG]

So it's exactly 67 G that have gone missing.

---

### Post by coffeecat on 2012-06-24
> **anbelo said:**
> 
So it's exactly 67 G that have gone missing.

Not quite. Disk Utility reports in Gigabytes (base 10: 1GB = 1,000,000,000 bytes) and df in Gibibytes (base 2: 1GiB = 1024x1024x1024 bytes). Your 812GB (gigabyte) partition is equal to 756GiB (gibibytes) so there's still a discrepancy of 11Gib for which I can't think of a reason offhand.

What does Disk Utility tell you about the sizes for sda2 and sda6? Apart from the discrepancy caused by reporting in GB, do they show a difference too?

---

### Post by anbelo on 2012-06-24
Thank you very much for the clarification, cofeecat.

For sda2 and sda6 I have:

df -h
sda2 99 GiB = 106.3 GB
sda6 23 GiB = 24.7 GB

Disk Utility
sda2 107 GB
sda6 25 GB

I have also looked for the missing Incoming files in the lost+found directory, but they're not there (du -h lost+found returns 29M).

---

### Post by anbelo on 2012-06-25
Don't know if it's related to the problem, but Disk Utility shows the following message for the logical partition that contains /home: "**WARNING:** The partition is misaligned by 1024 bytes. This may result in very poor performance. Repartitioning is suggested."

---

