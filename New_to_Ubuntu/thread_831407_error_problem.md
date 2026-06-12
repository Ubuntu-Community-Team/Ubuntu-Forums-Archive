---
title: "error problem"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by glb48 on 2008-06-16
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.how do i fix this

---

### Post by avtolle on 2008-06-16
From the terminal (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```

---

### Post by glb48 on 2008-06-16
dpkg: status database area is locked by another process
now it shows this

---

### Post by RomeReactor on 2008-06-16
Did you make sure no other package manager is open? Try running the command again.

---

