---
title: "evolution update freezes pc"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by -random on 2008-09-23
Yo! I downloaded the latest updates, and when it came to the 'setting up' part, evolution updating part cauzed my pc to freeze.

I restarted and got the following msg:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

did that and it froze again.

How do I fix this pls?

Can I remove evolution b4 the update is complete now? (i'm gonna remove evolution anyway..)

Thknxz

---

### Post by Mornedhel on 2008-09-23
dpkg does not take care of dependencies. Use apt-get instead :

sudo apt-get --purge remove evolution .

dpkg is pretty low-level. You shouldn't have to use it in most cases.

---

### Post by -random on 2008-09-23
thanks :D

solved!

---

