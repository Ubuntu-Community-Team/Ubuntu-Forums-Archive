---
title: "Hybrid drives"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by Dr. McKay on 2014-01-22
Does Ubuntu (or Linux in general) support the use of hybrid drives (HDD with SSD cache) ?
When you for example install Ubuntu on such a drive, will that drive be seen as one drive or two separate ones ? In other words, does the SSD caching work on Linux ?

---

### Post by fantab on 2014-01-22
AFAIK, NO.

You will have problems installing Ubuntu to such a 'Hybrid setup'. Only workaround is to disable 'cacheing' and only then will Linux install.

---

### Post by mcduck on 2014-01-22
Depends on the hard drive. Some of them use the drive's own controller to determine what data to cache, and therefore work on any operating system. Others use specific software to do this job and will therefore only work on operating systems where their software is made available.

As far as I know most of the hybrid drives available use the self-optimized way and therefore work just fine on Ubuntu, but you probably want to be a bit careful when selecting the drive just to be sure.

---

