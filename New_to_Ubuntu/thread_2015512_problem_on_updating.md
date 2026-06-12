---
title: "problem on updating"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by royalprakash on 2012-07-03
hi i use ubuntu 10.04 LTS.i'm tring to update or install any package by
comment but it display

cannot open lock file at /var/.../list/lock.
and cannot lock file List.

i gone that location that file had a X mark.
and try to change the permission but i can't.
what shall i do????

---

### Post by jmfal on 2012-07-03
Try running this then update/install:

```
  sudo rm /var/lib/dpkg/lock     
```

---

