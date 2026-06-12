---
title: "df command output"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by paichkash on 2012-08-09
my system is showing me the df output as  .. what the various directories mean ? are these seperate partitions like c drive,drive in windows ?

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36985736   9736640  25370296  28% /
tmpfs                   254188         0    254188   0% /lib/init/rw
varrun                  254188       220    253968   1% /var/run
varlock                 254188         0    254188   0% /var/lock
udev                    254188       164    254024   1% /dev
tmpfs                   254188        76    254112   1% /dev/shm
lrm                     254188      2192    251996   1% /lib/modules/2.6.28-19-generic/volatile
/dev/sdb5             27184720  26815536    369184  99% /media/SOFT
/dev/sdb1             12819836  12028748    791088  94% /media/WIN
/dev/sdb6             40017880  38868680   1149200  98% /media/WIN_
```

---

### Post by oldos2er on 2012-08-09
Post moved to its own thread.

---

### Post by Kalanac on 2012-08-09
Take a look at

```
man df
```

for an explanation of the df command.  You can do this with most commands :)

You can check your drives and partitions with fdisk

```
sudo fdisk -l
```

sda, sdb, sdc etc are drives, sda1, sda2, sda3 are partitions of a drive.  You can check where each of these are being mounted (if at all) by typing

```
mount
```

the partitions listed in fdisk will be shown as /dev/sda1 or similar.

From the list you posted

/dev/sda1 is mounted at / and is your root file system

/dev/sdb5
/dev/sdb1
/dev/sdb6

Are partitions on a separate drive to your linux file system and from the usage percentages they look pretty full.  As to the others, they appear to be magical mystery system mounts which are probably very important to the function of your computer, I'd leave them alone :)

---

