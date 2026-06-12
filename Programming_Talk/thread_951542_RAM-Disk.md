---
title: "RAM-Disk"
date: 2008-10-18
forum: Programming Talk
---

### Post by j4m on 2008-10-18
Hi,

  Can anybody tell me how to load search indexes on a RAM as they can be accessed a lot faster. (Using BASH scripts).

Thanks.

---

### Post by iponeverything on 2008-10-18
To create one thats a Gig and to mount it under /mnt/ramdisk :

```

mkdir /mnt/ramdisk
sudo mount -t tmpfs tmpfs /mnt/ramdisk -o size=1G,nr_inodes=200k,mode=01777

```

---

