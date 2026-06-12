---
title: "&quot;df&quot; command question regarding mout point"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by cheeky_lankan on 2008-09-10
i ran a "df -h " command and it spat out this :[http://paste.ubuntu.com/45448/;](http://paste.ubuntu.com/45448/;) my question is this..are the names under the files system, mounting point  or partitions. ?

thank you 

cheeky lankan

---

### Post by bobnutfield on 2008-09-10
This shows the amount of disk usage for your linux partitions in human readable terms (i.e. in gigabytes or megabytes.)  The mount points shown are where the partitions are mounted in your linux installation.  The tempfs is just that, temporary and is empty when you restart your system.

---

### Post by bab1 on 2008-09-10
The  "Filesystem" headings are partitions.  The "Mounted on" are the mount points.  The varlock, varrun, udev, devshm and lrm are for the VFS (virtual file system) See below --

```

me@there:~>df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              17G  2.7G   14G  17% /
varrun                173M  216K  173M   1% /var/run
varlock               173M     0  173M   0% /var/lock
udev                  173M   52K  173M   1% /dev
devshm                173M     0  173M   0% /dev/shm
lrm                   173M   34M  139M  20% /lib/modules/2.6.22-15-generic/volatile
/dev/sda3             5.9G  486M  5.2G   9% /home
/dev/sda4              50G   33G   14G  71% /smb


```

---

### Post by cheeky_lankan on 2008-09-10
> **bab1 said:**
> The  "Filesystem" headings are partitions.  The "Mounted on" are the mount points.  The varlock, varrun, udev, devshm and lrm are for the VFS (virtual file system) See below --

```

me@there:~>df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              17G  2.7G   14G  17% /
varrun                173M  216K  173M   1% /var/run
varlock               173M     0  173M   0% /var/lock
udev                  173M   52K  173M   1% /dev
devshm                173M     0  173M   0% /dev/shm
lrm                   173M   34M  139M  20% /lib/modules/2.6.22-15-generic/volatile
/dev/sda3             5.9G  486M  5.2G   9% /home
/dev/sda4              50G   33G   14G  71% /smb


```


Oh ok thank your for your explanation i understand it; are th the partitions of the varrun, varlock of the virtualsystem temporary; like do they get partioned and mounted when the system boots up again ?

---

