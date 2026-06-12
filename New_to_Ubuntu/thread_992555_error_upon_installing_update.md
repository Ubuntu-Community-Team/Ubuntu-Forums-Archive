---
title: "error upon installing update"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by catniko on 2008-11-24
Hello  I am new to Linux and Ubuntu.

When I went to install avaliable updates,  I got this error message:
An error occured the following  details are provided:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How can I fix this?  Any help is appreciated!

Thank you.

--Kristin

---

### Post by taurus on 2008-11-24
Close the update window first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by jemate18 on 2008-11-24
I, again believe this thread is SOLVED, please mark it SOLVED.

Thanks again....

---

### Post by catniko on 2008-11-25
Thanks!  That helped alot.

---

