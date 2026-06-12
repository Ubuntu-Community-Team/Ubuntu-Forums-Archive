---
title: "partitioning an external HDD: advice needed"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Stefanie on 2008-05-23
ok here i am again with another question... i want to buy a western digital my book external hard drive (1TB). first of all: will this work in ubuntu? 

i also wonder if i can partition the drive. my boyfriend will use it too and i don't want his windows viruses messing up my files. so i was thinking about making two partitions, one ntfs for his windows and one ext3 for my ubuntu. is this possible? will the drive work on both OS? how should i do it? i've used gparted before but i don't know if it is safe to use on an external hdd.

thanks a lot for anwering my questions :)

---

### Post by smurphy_it on 2008-05-23
Yes that will work.  Just use gparted, you will be fine.

---

### Post by neurostu on 2008-05-23
Yes gparted will work on an externall HDD. However keep in mind that if a virus gets onto the NTFS partition it could potentially destroy the ext3 data as well.  The virus could edit the partition table on the drive, the virus might come with support to read ext3 partitions.  This is the same problem people can have with a dual boot systems, windows viruses writing over ubuntu files.

---

### Post by Stefanie on 2008-05-23
> **neurostu said:**
> Yes gparted will work on an externall HDD. However keep in mind that if a virus gets onto the NTFS partition it could potentially destroy the ext3 data as well.  The virus could edit the partition table on the drive, the virus might come with support to read ext3 partitions.  This is the same problem people can have with a dual boot systems, windows viruses writing over ubuntu files.

oh i didn't know that. but i guess two different partitions is already a bit safer? 

i googled a bit for compatibility with ubuntu. it seems that some people experience problems with those mybooks, but most people say it will be ok after reformatting it to ext3. i hope this will be the case...

---

### Post by kilroy423 on 2008-05-23
You can partition the whole disk as ext3, there is a windows driver to read it: [http://www.fs-driver.org/](http://www.fs-driver.org/) .  You could also go with all ntfs, and use ntfs3g in ubuntu.

Kilroy

---

### Post by neurostu on 2008-05-23
So i personnaly haven't had any problems reading a NTFS partition in ubuntu. Go ahead and partition it into two drives, one NTFS and the other as EXT3, if you are going to be sharing data files on the drive you will either need to store those files on the NTFS partition or, install drivers to read ext3 in windows.

---

