---
title: "Raid 5"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by jaydinho on 2013-05-13
I have ubuntu 11.10 alternate installed on a 120gb hdd.

I then have 3 x 500gb hdd's configured with software raid 5.

Can I run this setup as I cant see the 3 drives but mdadm reports:

$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri May 10 21:58:21 2013
     Raid Level : raid5
     Array Size : 960056320 (915.58 GiB 983.10 GB)
  Used Dev Size : 480028160 (457.79 GiB 491.55 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon May 13 17:51:05 2013
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu:0
           UUID : f51a4e2e:ccaad19c:ab680f52:3387bf7d
         Events : 42

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1


I am a new to this and not sure how to make my 3 raid drives active?

Thanks

---

### Post by TheFu on 2013-05-13
It appears to be active already. Did you mount it?

BTW, 11.10 is out of support. It would be **smart to move to 12.04 **which gets 5 yrs of patches and support.  Do not use anything later if you arne't prepared to update the OS every 6 months.

---

