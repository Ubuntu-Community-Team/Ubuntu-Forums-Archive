---
title: "Mounting drives"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by stewils on 2008-05-08
I have three external usb drives connected to a samba server.  I've edited the fstab so that they mount automatically no problems.  The problem is upon restart of the pc, ubuntu gives the drives different names to the last time, so sbd3 might now be sbb3 etc...
I there any way i can ensure that the same drives are given the same names every time i boot?

---

### Post by sy88 on 2008-05-08
You could edit your fstab to identify each drive by UUID instead of by /dev/sdxy.  Just replace each device (ie. /dev/sda1) with it's UUID.  The format is "UUID=xxxx..." and may or may not include dashes (make sure there aren't spaces between the "=" signs).  The UUID's for currently mounted drives can be found by typing "ls -al /dev/disk/by-uuid"

---

### Post by sisco311 on 2008-05-08
mount the drives by uuid:

> /dev/sdb1 /mount/point     ext3    relatime,defaults        0       2-->

> UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /mount/point     ext3    relatime,defaults        0       2use the blkid command to get the uuid of the partition:
```
sudo blkid /dev/sdb1
```

---

### Post by stewils on 2008-05-09
Thanks for that guys.  Problem Solved.:KS

---

