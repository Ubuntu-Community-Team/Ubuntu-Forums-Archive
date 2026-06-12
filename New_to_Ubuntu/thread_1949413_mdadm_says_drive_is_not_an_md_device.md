---
title: "mdadm says drive is not an md device??"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by revmarkp on 2012-03-30
I have an /dev/md0 on an ubuntu 11.10 desktop as my /home drive. all fine until a power cut the other day.

/dev/sdb1 and /dev/sdc1 = /dev/md0 as a raid1:

```
root@server:/home/markp# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0]
      732571904 blocks [2/1] [U_]
```


```
root@server:/home/markp# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a796fd2c:740124f9:01f9e43d:ac30fbff (local to host server)
  Creation Time : Wed Jun 16 11:12:17 2010
     Raid Level : raid1
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Fri Mar 30 10:17:31 2012
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 3b16ed33 - correct
         Events : 7875134


      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
```

and

```
root@server:/home/markp# mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : a796fd2c:740124f9:01f9e43d:ac30fbff (local to host server)
  Creation Time : Wed Jun 16 11:12:17 2010
     Raid Level : raid1
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Tue Mar 27 11:25:22 2012
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 3b12f4a6 - correct
         Events : 7872549


      Number   Major   Minor   RaidDevice State
this     2       8       33        2      spare   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8       33        2      spare   /dev/sdc1
```

so /dev/sdc1 is showing as a spare - huh?

If I try and rebuild it it goes to about 20% and shows as a spare again?

tried to fail the drive but get this:
```
root@server:/home/markp# mdadm --fail /dev/sdc1
mdadm: /dev/sdc1 does not appear to be an md device

```

I'm obviously doing somthing wrong! After a while of running the partition get's 'wobbly' and i can't access it - it is backed up!

I tried booting up into a root shell and stopping /dev/md0 (worked ok), but again mdadm declares /sdc1 is not an md device when I try to fail it (tried --force option as well). if I physically remove either drive the array will not start??

Help appreciated

---

