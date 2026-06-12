---
title: "unable to view contents of ext3 usb drive"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Crustacean on 2012-07-12
Hello,
I have a fresh install of Ubuntu 12 on a new laptop and am having problems with viewing the contents of a USB drive.  The USB drive is a WD Passport with 2 partitions, a small fat32 partition and a large ext2 partition.  I was using this drive on an older laptop running Ubuntu 11.10 to hold backup files and music.  When I try plugging it into the new laptop the first user created on the system can see and browse both partitions, but the second user that was created can only browse the fat 32 partition.  I tried adding the second user to the groups plugdev, cdrom, and dip then relogging in as that user, but none of that solved the problem.  The partition does appear to be mounted as I can see it in Linux's filemanager, but when I try to access it I get permission denied.  I am having trouble understanding why the first user created can access it but not the second.

Any help would be greatly appreciated,

Crustacean

---

### Post by Lykopis on 2012-12-07
It appears to be a permissions problem. You can try this and see if it gives you access. Lets say your first user is crustacean and your second user is ubuntu2 now you would go to you users and look at the groups now add   ubuntu2 to   the crustacean group. Now you should be able to access the ext2 partition, albeit most likely in read only mode.

---

