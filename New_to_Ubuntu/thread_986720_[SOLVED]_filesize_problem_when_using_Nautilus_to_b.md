---
title: "[SOLVED] filesize problem when using Nautilus to burn DVD"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by BertP on 2008-11-18
I am trying to to burn a data DVD for the first time.  I am using Nautilus, invoked by choosing "CD DVD Creator" in the Ubuntu 7.10 "Places" menu.

So I drag a directory full of files to the Nautilus.  When I press the "Write To Disc" button , Nautilus pops up a window telling my my data size is 4.4 GiB.  When I press the window's "Write" button, I get a window that tells me:

Reload a rewriteable or blank disc.
Please replace the disk in the drive with a supported disk with at least 4.4 GiB free. The following disc types are supported: DVD +R DL
----

Why do I need a Double Layered DVD?  I thought single layered DVD capacity was about 4.7 GB and 4.4 should be well under that limit

---

### Post by nhasian on 2008-11-19
This is due to the classic difference between GB and GiB, KB and KiB.

Humans think 1KB = 1000 bytes while computers think 1 KB =1024 bytes (2 to the 10th power). To be more accurate (and avoid this confusion) 1024 bytes should be referred to as 1 KiB (kibibyte).

A DVD can hold approximately 4.7 GigaBytes (GB) but only 4.37 GibiBytes 

[http://wiki.answers.com/Q/Why_is_a_4.7GB_DVD_only_able_to_use_4.3GB](http://wiki.answers.com/Q/Why_is_a_4.7GB_DVD_only_able_to_use_4.3GB)

---

### Post by BertP on 2008-11-19
Thanks!   I trimmed the directory structure so that it held only 4.1 Gib and it worked fine!

---

