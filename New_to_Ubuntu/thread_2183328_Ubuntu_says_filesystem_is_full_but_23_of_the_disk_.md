---
title: "Ubuntu says filesystem is full but 2/3 of the disk is free"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by rbenet-4 on 2013-10-24
Hello,

I am a new to Ubuntu. 

I have created a Ubuntu 12.04 LTS virtual machine with 40GB of disk space in a Windows server. In the middle of some data import onto a database the process errored out due to lack of disk space (I had a warning minutes before that there was little disk space remaining).

The Disk Usage Analyzer utility shows that the filesystem is full though there is still 2/3 of the disk free. However when I run "df" I see that indeed there is about 2/3 of the disk free.

I have tried to use gparted but it appears that all 40GB are allocated and there is not free space to be allocated.

So I guess my question is why Ubuntu would say that the filesystem is full when there is still 2/3 of the disk free? And how can I make use of those 2/3 so I can continue my data import?

Thanks so much

---

### Post by TheFu on 2013-10-24
$ df -i

---

