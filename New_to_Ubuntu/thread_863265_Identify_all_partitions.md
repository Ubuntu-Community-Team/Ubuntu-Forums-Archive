---
title: "Identify all partitions"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-18
From within a running Linux partition on a hard drive, what is a good way to identify all other defined partitions on that hard drive?

---

### Post by Vivaldi Gloria on 2008-07-18
> **pgte3 said:**
> From within a running Linux partition on a hard drive, what is a good way to identify all other defined partitions on that hard drive?

```
sudo fdisk -l
ls /dev/disk/* -lah
sudo blkid
mount
```

---

### Post by Inxsible on 2008-07-18
> **pgte3 said:**
> From within a running Linux partition on a hard drive, what is a good way to identify all other defined partitions on that hard drive?
```
df -h
``` or ```
sudo fdisk -l
```

---

### Post by warp99 on 2008-07-18
Open a terminal and run:

```
sudo fdisk -l /dev/<system_name_of_drive>
```

that will list all of the partitions mounted or not mounted on that particular disk.

---

### Post by pgte3 on 2008-07-18
This is helpful, thanks.

---

