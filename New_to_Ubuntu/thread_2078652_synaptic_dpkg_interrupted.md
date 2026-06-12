---
title: "synaptic dpkg interrupted"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Troooppo stefano on 2012-10-31
Xubuntu is so good:popcorn:, but day in and day out something breaks! :confused:
Now I can't run synaptic
the error comes:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I pasted
       dpkg --configure -a
in the terminal, but the message was:

dpkg: error: requested operation requires superuser privilege


How can it be fixed??

Many thanks!

---

### Post by QIII on 2012-10-31
Add sudo before the command.

```
sudo dpkg --configure -a
```

---

### Post by Troooppo stefano on 2012-11-03
It works, great!

---

