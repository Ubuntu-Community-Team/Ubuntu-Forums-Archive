---
title: "Brand new drives.  Raid5 = Degraded"
date: 2015-11-04
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-11-04
So, I got my 14.04 LTS server up and running.  Got Owncloud set up properly.  I installed Webmin so to get a browser based admin panel.  From Webmin last night I can see my RAID Array status was "Clean".  This morning, I started uploading files to the Owncloud solution (using the Raid Array).  Now Webmin says the Array status is "Clean, Degraded".  I went into the details and it is reporting one of my drives has failed.

The beef is this.  These are BRAND NEW "NAS" drives.  The array was configured using the installation process.

Someone give me some guidance before I cram dynamite into the server and blow it up!  :?

```
/dev/md0:
        Version : 1.2
  Creation Time : Sat Oct 31 16:15:55 2015
     Raid Level : raid5
     Array Size : 1953258496 (1862.77 GiB 2000.14 GB)
  Used Dev Size : 976629248 (931.39 GiB 1000.07 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Nov  4 07:29:54 2015
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : Bulbous:0  (local to host Bulbous)
           UUID : 4220f158:86c32cd1:f033de30:18ca8d4e
         Events : 391

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5


```


> 
    Number   Major   Minor   RaidDevice State
       0       0        0        0_**      removed**_
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5

Why would it show that line item as "REMOVED"?  Additionally, if you read what I pasted above...  It doesn't show that any device "FAILED".  I'm new to all of this so perhaps I am misinterpreting things.

haha on the positive note.. I get to practice disaster recovery!  =P

---

