---
title: "How to mount my SD to my directory auto ?"
date: 2018-09-28
forum: New to Ubuntu
---

### Post by clancy.lian on 2018-09-28
Hi,

When I insert my SD card to the machine, it will auto mount to the path /media/xxxx . And I would want to it mount to my created directory. how can I modify the udev rules ? I can't find the rules which mount SD to /media/xxxx . 

Thanks.

---

### Post by krooknews on 2018-09-30
Hello Clancy, 

Please follow the below steps to mounting device

$ mount
(lists all currently mounted devices)

$ mount -t type device directory
(mounts that device)

for example (to mount a USB drive):
$ mount -t vfat /dev/sdb1 /media/disk

---

