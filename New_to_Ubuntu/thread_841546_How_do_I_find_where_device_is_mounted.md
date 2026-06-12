---
title: "How do I find where device is mounted"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-06-26
Hey everyone,
I was curious as to how I could easily find where a device was mounted to..

Thanks,
MishaTheGoat

---

### Post by DGortze380 on 2008-06-26
what kind of device? it should be listed in /etc/fstab

```
 cat /etc/fstab | less 
```

---

### Post by wootah on 2008-06-26
> **mishathegoat said:**
> Hey everyone,
I was curious as to how I could easily find where a device was mounted to..

Thanks,
MishaTheGoat

```
$> mount
```

---

### Post by drs305 on 2008-06-26
Run:
```
mount
```
to see where partitions are currently mounted.

Fstab shows where partitions listed in its file are mounted automatically at boot or mount points that are reserved for manually mounting partitions after boot.

---

