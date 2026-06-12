---
title: "Mistake on overlapped partition for Ubuntu installation"
date: 2017-03-30
forum: New to Ubuntu
---

### Post by gonasago on 2017-03-30
Originally, I had partitioned C: and D: drives for Windows 7.

Unfortunately, I installed Ubuntu on D:. However, luckily, it didn't format the data on D:.

When I use a partition recovery program (active partition recovery et...), all the data with folders are alive.

The problem is that I can't back up the data in D:.

Is there any possible way except for buying the commercial partition recovery program?

Thanks in advance.

---

### Post by yancek on 2017-03-31
The suggested method for installing Ubuntu is to leave unallocated space on the hard drive on which to install.  
If D was a windows partition, why would you try to install a Linux system there?  Exactly what method did you use to install Ubuntu?  Does anything boot? your windows 7?, the Ubuntu?

Testdisk and Photorec are free downloads which might be able to recover data.  Google either and you should get their site.

---

### Post by oldfred on 2017-03-31
C: & D: do not mean anything in Linux.
Post this:
sudo parted -l

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

