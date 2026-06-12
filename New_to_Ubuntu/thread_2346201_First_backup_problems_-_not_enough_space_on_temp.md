---
title: "First backup problems - not enough space on /temp"
date: 2016-12-12
forum: New to Ubuntu
---

### Post by Vaclav Vasek on 2016-12-12
My first usage of backup fails with this message 

Temp space has 34287616 available, backup needs approx 68157440.

I did checked similar posts and they all solve the issue by creating new disk partitions. 
I prefer NOT to do that at this point and would like to change the /temp  directory to a 1 TB partition instead. 
As a new user of Linux I do not want to mess things up and really do not know how or if it is even possible to move the /temp. 
Help would be appreciated.

---

### Post by mastablasta on 2016-12-13
what is the backup app being used?

---

### Post by Vaclav Vasek on 2016-12-13
Using System Setting -  "Backup"

---

### Post by mastablasta on 2016-12-14
thta's probably deja dup then: [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

you can try another app. not sure why /temp would be limited unless it is on another disk partition.

Duplicati or Luckybackup work well. then there are also Backintime, Areca and similar apps (assuming you want a GUI for the app).

---

### Post by vasa1 on 2016-12-14
Could you share the output of
```
df -h
```
to give people an idea of your set up? Then you can point out what you want to back-up and to where.

---

### Post by Vaclav Vasek on 2016-12-14
```
jim-desktop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           375M  6.2M  369M   2% /run
/dev/sda5        47G   44G  531M  99% /
tmpfs           1.9G  240K  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           375M   56K  375M   1% /run/user/1000
/dev/sdb6        62G  6.6G   56G  11% /media/jim/OpenCameraB
/dev/sdb5        40G   31G  9.1G  77% /media/jim/Programs
/dev/sdb8       106G   68M  105G   1% /media/jim/0822C8912019FFC8
/dev/sdb7       443G   51G  393G  12% /media/jim/Ex Drive Co
/dev/sdb1       415G   86G  330G  21% /media/jim/Photo Album
/dev/sdb3       1.3T   77G  1.2T   7% /media/jim/Copy_Arduino_Programs
jim@jim-desktop:~$ 

```
Here it is and I KNOW it is a grand mess.
I have some leftovers from my attempt to do RAID. 

the /dev/sdb1 is UNTOUCHABLE for now 

I like to move the /temp to /dev/sdb3 for now , if suggested I'll make it a separate partition later. 

Just found out that I need also to extend 
/dev/sda5        47G   44G  531M  99% /

I hope Santa will bring another xTB drive so I can EVENTUALLY reorganize.

 Thanks for helping

---

