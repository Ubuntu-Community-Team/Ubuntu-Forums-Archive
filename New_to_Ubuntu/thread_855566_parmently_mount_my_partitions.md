---
title: "parmently mount my partitions"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by nnamdi on 2008-07-10
hello pls how do i parmently mount my partition on ubuntu thanks

---

### Post by tech9 on 2008-07-10
> **nnamdi said:**
> hello pls how do i parmently mount my partition on ubuntu thanks

your HD should mount permanently after creating the partition.

post
```
sudo fdisk -l
```

---

### Post by Elfy on 2008-07-10
Probably needs to be added to fstab - can you post it please

```
cat /etc/fstab
```

---

