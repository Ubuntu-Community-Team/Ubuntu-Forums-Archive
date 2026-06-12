---
title: "why tmpfs is only twice quicker than hard disk?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by phdmybest on 2008-09-23
i ceate a tmpfs ramdisk.
when i test tmpfs ramdisk with dd command like this&#65306;
dd if=/dev/zero of=/test/test.file bs=1M count =1024.

i got a result 1.6gb/s.

i did the same operation on my hard disk,then i got the result 
639mb/s.

it seems like that tmpfs is only twice quicker than hard disk.

But is this could be true?

Or there are something wrong in my test ?

anybody could help ?

thanks in advanced.

---

### Post by Sef on 2008-09-24
moved to absolute beginners.

---

### Post by nowshining on 2008-09-24
> **phdmybest said:**
> i ceate a tmpfs ramdisk.
when i test tmpfs ramdisk with dd command like this&#65306;
dd if=/dev/zero of=/test/test.file bs=1M count =1024.

i got a result 1.6gb/s.

i did the same operation on my hard disk,then i got the result 
639mb/s.

it seems like that tmpfs is only twice quicker than hard disk.

But is this could be true?

Or there are something wrong in my test ?

anybody could help ?

thanks in advanced.

perhaps because it's in RAM??

---

### Post by freak42 on 2008-09-24
unless you did your tests on a very high-end server with enterprise 15000 rpm harddisks (possibly) in a raid configuration, your hd throughput measurement seems extremely high.

Roughly normal consumer harddisks have a throughput anywhere from 20-100 MB per second.

hth

---

### Post by nowshining on 2008-09-24
> **freak42 said:**
> unless you did your tests on a very high-end server with enterprise 15000 rpm harddisks (possibly) in a raid configuration, your hd throughput measurement seems extremely high.

Roughly normal consumer harddisks have a throughput anywhere from 20-100 MB per second.

hth

either that or they are measuring disck cache :) via hdparm

---

### Post by jdong on 2008-09-26
nowshining's on the right track:

Both operations are being accelerated by available system RAM: Your "639mb/s" rate is only because probably around 600MB of cache RAM was used to buffer the 1GB of data you were writing, until the Linux kernel felt it was a better idea  to start writing that buffered data to disk rather than hog RAM that other applications could need.

tmpfs is going to be faster than RAM in any case because it keeps track of fewer structures (after all, it was designed to be temporary in nature) as opposed to any on-disk filesystem.

If you want a true measurement of on-disk, run "sync" after your dd command and time how long that takes, too. Should take around 20-30 seconds on the disk version.

---

