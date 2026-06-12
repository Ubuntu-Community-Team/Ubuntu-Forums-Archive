---
title: "Update problems"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by ginderhulk on 2008-06-12
I accidentally turned my computer off when Ubuntu was installing updates. Now when I try ti install then again I get this error message...


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


how do i fix it?

P.s. 
I am kind of new to linux so I will ned help with commands

---

### Post by perlluver on 2008-06-12
> **ginderhulk said:**
> I accidentally turned my computer off when Ubuntu was installing updates. Now when I try ti install then again I get this error message...


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


how do i fix it?

P.s. 
I am kind of new to linux so I will ned help with commands

Open up a terminal and type sudo dpkg --configure -a.

---

