---
title: "Check Hard Drive Sizes"
date: 2009-10-27
forum: Programming Talk
---

### Post by EMCGFX on 2009-10-27
Small function to check hard drive sizes, nothing special really :D

```
# Check Hard Drives Space
function space() {
  echo ''
  df -h /dev/sda3
  df -h /dev/sdb1
  df -h /dev/sdc1
  df -h /dev/sdd1
  df -h /dev/sde1
  echo ''
}
```

---

### Post by kidders on 2009-10-28
Hi there,

Thought you might appreciate some other suggestions ...

You could probably just run **df -h /dev/sd[a-z][1-9]** instead, to avoid hard-coding a list of partitions. Even better, you could limit the list to mounted filesystems (to stop df mis-reporting disk space) with something like ...```
cut -d" " -f1 /etc/mtab | grep '/dev/[hms]d[a-z][1-9]*' | xargs df -h
```

---

