---
title: "New Installation"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by bern1939 on 2008-05-25
Since I arrived at a point where the disk space for Ubuntu exceeds 43GB-(the upper limit) on /dev/sda1 and I am now having problems with my printer and network.......everything seems to have gone wrong! I am going to install the new 8.04 version.

I am using an entire disk for Ubuntu (70GB)

My question is......can I install the new version and ensure that all my data, currently stored on /dev/sda3 is retained???

How can I do that if I tell the new installation to use the entire disk to install?


Thanks


Bern

---

### Post by Abu_Dayya on 2008-05-25
I'm not sure I understand what you're saying. You want to re-install ubuntu on your hard disk which is sda1, and you also want to resize it. But you don't want to change your data on sda3. Am I right? 

Becuase if thats the case, it can be done. when you boot from your ubuntu cd, and you go to the point where the partition manager starts, chose manual installation. You'll see all your disk partitions (i.e sda1, sda2, ...), and you can chose to install ubuntu on sda1 from there, and it won't change sda3. But be aware NOT to click on "Build new partition table". That will erase the entire disk's contents.

Hope that helps...

---

### Post by bern1939 on 2008-05-25
Thanks very much I will try that.

Bern

---

