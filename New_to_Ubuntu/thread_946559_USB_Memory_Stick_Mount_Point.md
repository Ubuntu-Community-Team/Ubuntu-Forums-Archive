---
title: "USB Memory Stick Mount Point"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-10-13
I have a USB memory stick which automounts as /media/disk, how do I find out how this is mounted ie /dev/sda1 or whatever.

---

### Post by jbrown96 on 2008-10-13
```
sudo fdisk -l
``` in a terminal will list your devices. You should be able to find it in there. It will most likely be the only device that has only one partition.

---

