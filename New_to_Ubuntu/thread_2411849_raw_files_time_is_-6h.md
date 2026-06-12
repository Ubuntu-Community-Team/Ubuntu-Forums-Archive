---
title: "raw files time is -6h"
date: 2019-02-04
forum: New to Ubuntu
---

### Post by smsmith050 on 2019-02-04
Camera raw files show a modify time of -6h on my ubuntu system.
On OSX the modify time is correct.
On the cameras the time is correct.

Photos taken 14:17
ls -l canon sd card 
-rw-r--r-- 1 xxxxx xxxxx 21309856 Feb  4 08:17 IMG_9040.CR2
-rw-r--r-- 1 xxxxx xxxxx 21321882 Feb  4 08:17 IMG_9041.CR2
-rw-r--r-- 1 xxxxx xxxxx 21329693 Feb  4 08:17 IMG_9042.CR2
-rw-r--r-- 1 xxxxx xxxxx 21334618 Feb  4 08:17 IMG_9043.CR2
Photos taken 13:37
ls -l nikon sd card
-rw-r--r-- 1 xxxxx xxxxx 33070883 Feb  4 07:37 DSC_6933.NEF
-rw-r--r-- 1 xxxxx xxxxx 33091558 Feb  4 07:37 DSC_6934.NEF
-rw-r--r-- 1 xxxxx xxxxx 33123154 Feb  4 07:37 DSC_6935.NEF

lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

timedatectl 
                      Local time: Mon 2019-02-04 14:41:37 CST
                  Universal time: Mon 2019-02-04 20:41:37 UTC
                        RTC time: Mon 2019-02-04 20:41:37
                       Time zone: America/Chicago (CST, -0600)
       System clock synchronized: yes
systemd-timesyncd.service active: yes
                 RTC in local TZ: no

---

### Post by smsmith050 on 2019-02-04
A flash drive with a txt file modified on OSX shows a 6hr difference modified time on ubuntu. Its is not a RAW file issue. Seems related to drives mounted at /media.

---

### Post by smsmith050 on 2019-02-09
Is the modified time shift I see related to the system using UTC internally ?

uname -v #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019

A file modified at 09:27 AM on OSX shows Feb  9 03:27  time.rtf a six hour earlier time on ubuntu. 

stat time.rtf
  File: time.rtf
  Size: 339       	Blocks: 32         IO Block: 16384  regular file
Device: 851h/2129d	Inode: 20612       Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/  xxxxxx)   Gid: ( 1000/  xxxxxx)
Access: 2019-02-08 18:00:00.000000000 -0600
Modify: 2019-02-09 03:27:50.000000000 -0600
Change: 2019-02-05 13:28:24.010000000 -0600
 Birth: -

I assume ubuntu cannot read the modified time that osx puts on the file without subtracting 6hr from the osx time.

---

### Post by dmnur on 2019-02-09
It's because the file system used on these SD cards or cameras themselves store modification dates in local time, but Ubuntu expects them to be in UTC.
Your system is set up to CST (UTC-6), and Ubuntu subtracts six hours from the dates, which is an expected behavior.

What file system is used? Show the output of **mount** command.

---

