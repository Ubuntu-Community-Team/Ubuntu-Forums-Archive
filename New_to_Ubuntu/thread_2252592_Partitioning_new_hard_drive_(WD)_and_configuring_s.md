---
title: "Partitioning new hard drive (WD) and configuring standy/sleep"
date: 2014-11-13
forum: New to Ubuntu
---

### Post by rene98c on 2014-11-13
Building a small itx system and i want to setup this box as broadband router/entertainment box/file server and Lubuntu was interesting find that could host all these things well.

But as this box will be in my living room and i plan to attach two WD 4TB red drives on it and i want it to be quiet if drives are not accessed .
So currently i am having problems telling drive to keep quiet.

I have tried hdparm, hd-idle, wdidle3-tools but have'nt figured out solution yet.
Googling on the matter revealed to me that WD does'nt play well with these tools.

So question is actually regarding file systems in regard to these tools.
When i partitioned my hard drive in ntfs and mounted it, hd-idle seemed to work fine, but on linux i would prefer linux file system so i formatted drive to ext4 
and when i mounted the drive hd-idle ,neither hdparm -y , nothing seemed to spin down the disk.

So something is going on with the drive when mounted, or is hdparm supposed to work only if drive is unmounted? 
i used iotop to see what is going on with the drive , but it does not show what drive and what is accessed, havent found tool for that yet.

Maybe i am rushing things, maybe freshly formatted ext4 hard drive needs time to calm down (journaling doing its stuff?) before hd-idle/hdparm can kick in?

Edit 1.0:
journaling doing its job may be indeed keeping my drive busy : [http://askubuntu.com/questions/402785/writes-occurring-to-fresh-ext4-partition-every-second-endlessly-cause-and-solut](http://askubuntu.com/questions/402785/writes-occurring-to-fresh-ext4-partition-every-second-endlessly-cause-and-solut)
6h at least for 4TB, so i'll just have to wait.

---

### Post by jtarin on 2014-11-14
I've got several large disk for movies and my experience is I've had better luck with NTFS......just my opinion.

---

