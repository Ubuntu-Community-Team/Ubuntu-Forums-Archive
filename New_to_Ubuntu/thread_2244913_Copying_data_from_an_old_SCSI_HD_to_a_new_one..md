---
title: "Copying data from an old SCSI HD to a new one."
date: 2014-09-19
forum: New to Ubuntu
---

### Post by ampryler on 2014-09-19
Hi everyone,
I'm a newbie about Ubuntu so I need some help from you guys. At work I  have an old PC with Ubuntu 12.04 which I'll use to clone,copy or do back  ups from some really old SCSI HDD to a new ones. We have a testing  machine, for aviation equipment, that runs with UNIX. All the hard  drives are formatted and loaded with an UNIX based program which I have  to back it up to a new SCSI HDD. Somebody told me to use Linux to do it  so that's what I did but now I don't have any clue how to copy all the  information from the old (and small hard drive) to a new (and bigger  one). I ordered the SCSI card (Adaptec 2940) cables, adapters and  everything I can think of to make it possible. I need to transfer the  information from 2 HDD to just one and back this one up with all test  programs.Any information and help will be more than welcome,thank you  !!!!

---

### Post by tgalati4 on 2014-09-20
```
sudo cp /dev/sda /dev/sdb
```

This assumes /dev/sda is the name of the old SCSI drive and /dev/sdb is the name of the new SCSI drive--the same size or larger.

Use *gparted* to fix the paritions.  It will say something like "Partition does not match physical size of the disk.  Would you like to fix?"  Why yes.  Swap drives and boot.

Putting two drives into one can be a little tricky, but you can create two partitions in the new drive and simply copy one drive to the first partition and the second drive to the second partition.  Then pull the programs from the second into the first.  Those commands would look like:

```

sudo fdisk -l
sudo cp /dev/sda /dev/sdb1
(swap old drives)
sudo cp /dev/sda /dev/sdb2
```

You would need to format the new drive with two equal partitions in *gparted* in the correct format type--probably ufs, but you will have to research what file system you have on the old drives.

Use the file manager (Nautilus or Caja) to pull the files from the second partition into the first.  Then you can wipe the second partition and use it as a backup partition in the future.

Remind me not to fly on any planes tested with this system.

---

### Post by ampryler on 2014-09-20
Thank you so much for your help, I'll work with this on Monday. I was also looking to work with Clonezilla and have 2 different backup drives instead of complicate things and try to transfer everything to one and then back it up. 
Thanks again....

---

### Post by sandyd on 2014-09-20
Moved to *New to Ubuntu*

---

### Post by ampryler on 2014-09-20
OK, I had it there also but no replies yet that's why I posted it here, sorry.

---

