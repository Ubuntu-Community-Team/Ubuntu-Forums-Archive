---
title: "Disk usage"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by gopukrishnan on 2014-04-08
Hi,

I just crated a cloud server in Rackspace. i am little bit confused about the filesystem. I can see one partition /dev/xvda1 is mounted in '/' which is having size 20G and used space only 628 M. 

1. What is all these '**none**' which is mounted in /dev,/dev/shm,/var/run,/var/lock and /lib/init/rw respectively ? From where it got all these space since only one partition /dev/xvsda1 is there ? (/dev/xvdc1 is swap I guess)

2. When I checked the 'df -h' first time, I got an extra entry :
[B]Filesystem            Size  Used    Avail    Use%       Mounted on
none[/B]                   **20G**  628M   19G     4%         [B]/var/lib/ureadahead/debugfs
[/B]whch didnt come for the same command afterwards. What is this entry and from where it got 20 GB space ?

3. How can I find how much disk space is a partition using from 'fdisk -l' command ? Only block size is mentioned and how can it be converted into MB or GB ?
Eg :
Disk /dev/xvdc: 1073 MB, 1073741824 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/xvdc1         1        1886     1048575+  83  Linux

See below the below outputs if you need :

************************************************
root@gopu1:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             20G  628M   19G   4% /
**none**                  493M  128K  493M   1% /dev
**none**                  498M     0  498M   0% /dev/shm
**none**                  498M   36K  498M   1% /var/run
**none**                  498M     0  498M   0% /var/lock
**none**                  498M     0  498M   0% /lib/init/rw
**none**                   **20G**  628M   19G   4% **/var/lib/ureadahead/debugfs**

************************************************

************************************************
root@gopu1:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/xvda1             20G  628M   19G   4% /
**none**                  493M  128K  493M   1% /dev
**none**                  498M     0  498M   0% /dev/shm
**none**                  498M   36K  498M   1% /var/run
**none**                  498M     0  498M   0% /var/lock
**none**                  498M     0  498M   0% /lib/init/rw

***********************************************

***********************************************
root@gopu1:~# fdisk -l

Disk /dev/xvdc: 1073 MB, 1073741824 bytes
139 heads, 8 sectors/track, 1885 cylinders
Units = cylinders of 1112 * 512 = 569344 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee1c7

    Device Boot      Start         End      Blocks   Id  System
/dev/xvdc1               1        1886     1048575+  83  Linux

Disk /dev/xvda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a4d5

    Device Boot      Start         End      Blocks   Id  System
/dev/xvda1               1        2611    20970496   83  Linux
***************************************************


Thanks,

---

### Post by TheFu on 2014-04-08
Linux uses "virtual file systems" as a way to help run the system. That's what all those other entries are.  Look inside /proc/ to see current system data.

fdisk is deprecated due to GPT disks. That probably doesn't matter inside a VM, but it is a good habit to use **parted** instead.  These tools do NOT show used storage.  Use df / dh for that.  Here's my netbook with those virtual file systems removed:
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        84G  7.5G   72G  10% /
/dev/sda15       18G   44M   17G   1% /Data
istar:/D        3.0T  2.2T  737G  75% /D
```

If you want to learn the specifics of any command, check the "man page" actually on the system - **man fdisk** will explain.   Different versions of every command can work a little differently - the version of fdisk on my system has different defaults than on the rackspace version. I'm guessing this because on my system, it shows Kb by default.

---

