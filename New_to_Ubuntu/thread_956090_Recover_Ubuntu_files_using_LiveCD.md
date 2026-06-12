---
title: "Recover Ubuntu files using LiveCD"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Sunshine1987 on 2008-10-22
.

---

### Post by Christmas on 2008-10-23
If your PC doesn't boot and you want to recover files using LiveCD you need to mount the partitions on which your data is located, e.g.:
```
mount -t ext3 /dev/sda1 /mnt/empty_directory
```

---

