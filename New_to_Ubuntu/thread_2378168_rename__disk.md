---
title: "rename  disk"
date: 2017-11-20
forum: New to Ubuntu
---

### Post by jarp53 on 2017-11-20
when i install Ubuntu i use an USB stick and install in a 60 gb  ssd , but now i would like to rename it (ubuntu) , is there a way i can do this ?

---

### Post by Dennis N on 2017-11-20
Use gparted to create **names** for partitions or **labels** for file systems. In gparted, select the partition, then:

Menu > Partition > Name Partition
or 
Menu > Partition > Label File System 

Names only can be created on GPT partitioned disks!

Disks don't get named or labeled. Just partitions or the file systems on them.

---

### Post by jarp53 on 2017-11-23
Menu > partition > label file system ; that work for me thank you

---

