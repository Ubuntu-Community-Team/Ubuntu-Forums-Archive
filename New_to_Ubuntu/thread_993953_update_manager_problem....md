---
title: "update manager problem..."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by heroidi on 2008-11-26
when i try to install updates it displays a window in wich is written:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


what do i have to do :(

---

### Post by taurus on 2008-11-26
Close the update window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by heroidi on 2008-11-26
thanks man before you told me i tried to write in terminal sudo dpkg --configure -a 
thanks for filling it with sudo apt-get update manager

---

