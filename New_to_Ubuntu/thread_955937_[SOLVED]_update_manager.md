---
title: "[SOLVED] update manager"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-22
I tried to update an got the message:
E:dpkg was interupted,you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open failed(),please report.
How do I do this,how do I fix?

---

### Post by duruttye on 2008-10-22
Did you run manually **dpkg --configure -a**?

---

### Post by kostkon on 2008-10-22
> **johntravis said:**
> I tried to update an got the message:
E:dpkg was interupted,you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open failed(),please report.
How do I do this,how do I fix?
Open a terminal (*Applications -> Accessories -> Terminal*) and give
```
sudo dpkg --configure -a
```
it will ask you for a password, give yours.

---

### Post by johntravis on 2008-10-22
new pop-up
You have one broken package on your system
Use the "broken" filter to locate it.

---

### Post by duruttye on 2008-10-22
Try:
System > Administration > Synaptic package Manager > (password) > Edit > Fix broken packages!

---

