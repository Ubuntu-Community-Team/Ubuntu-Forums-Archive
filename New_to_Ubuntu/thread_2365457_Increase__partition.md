---
title: "Increase / partition"
date: 2017-07-06
forum: New to Ubuntu
---

### Post by ghanekaranand on 2017-07-06
Here are some details about my installation:
Ubuntu 14.04.5 LTS

df -m
```
Filesystem     1M-blocks  Used Available Use% Mounted on
udev                3939     1      3939   1% /dev
tmpfs                790     2       789   1% /run
**/dev/sda11          5505  4366       837  84% /**
none                   1     0         1   0% /sys/fs/cgroup
none                   5     0         5   0% /run/lock
none                3950     1      3949   1% /run/shm
none                 100     1       100   1% /run/user
```


Partition details attached in the screenshot[ATTACH=CONFIG]275898[/ATTACH]

When I try to update the ubantu version, I keep getting error about insufficient disk space. Though I have few GB unallocated diskapce, I am unable to make it avaiable to / parition. Can you please suggest how I can increase the avaiable space on / partition?

---

### Post by Dennis N on 2017-07-07
95% of your disk is allocated to Windows sda2, leaving 931 - 887 = 44 gB for other purposes. Have you done the math? You could delete partitions 6,7,8,9,10 and free a block of unallocated space. Roughly 17 gB available from 6,7,8,9,10 as I calculate it. Then, expand your sda11 to the right, except leave a small amount for a swap partition on the right of the expansion. How about that?

---

### Post by Dennis N on 2017-07-07
Assuming you do this, your new swap will have a different UUID, so after creating it, edit and change the UUID in /etc/fstab of your OS on sda11, or you will have some problems when you start it up. All work here being done from a live cd, or course.

---

### Post by Impavidus on 2017-07-07
You have 5 small ext4 partitions, each of them too small for a useful Ubuntu system. I suggest the following:
- Make backups of your files on the Linux partitions. It can't be much.
- Boot Windows and run a file system check on sda2, your Windows partition. Delete all Linux partitions, move sda4 (if you want to keep it), optionally shrink sda2, move partitions around to get all unallocated space in one chunk.
- Reboot Windows a couple of times to let it run all its file system checks.
- Boot an Ubuntu live disk, create a single ext4 partition and a swap partition and do a fresh install of Ubuntu 16.04 LTS.

Extensive shuffling of partitions and upgrading your Ubuntu at the same time is just too risky compared to the small rewards. Sometimes it's just better to format and reinstall. Always keep in mind that it's best to use Windows tools for Windows partitions and Linux tools for Linux partitions.

---

### Post by oldfred on 2017-07-07
Gparted does not show your NTFS partition use. And it has red ! icon saying it sees something wrong.
Typically that is either Windows needs chkdsk which could be from an abnormal shutdown or from a partition resize. Or that it is a newer Windows 8 or 10 and you have fast start up or hibernation still on. 

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by johndough2 on 2017-07-07
Hi

Very tiny on my mobile, however I see extended. If you are in the old MBR  you may have run out of partitions not space.  So the excellent advice to  combine the small ones is sound.

---

