---
title: "Add/Remove Application problem"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by BRFC on 2008-08-30
Help people when I try to use Add/Remove all I get is this mesage, 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Help.

---

### Post by Canis familiaris on 2008-08-30
Go to terminal: (Applications->Accessories->Terminal)
```
sudo dpkg --configure -a
```

And after execution of the command, run Add/Remove Again.

---

### Post by hopkinsjeni on 2008-08-30
Please see my thread:
[http://ubuntuforums.org/showthread.php?t=884172]("http://ubuntuforums.org/showthread.php?t=884172")
It was exactly the same problem in the end.
Hope it helps

---

