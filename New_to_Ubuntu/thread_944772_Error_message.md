---
title: "Error message"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by scooop08 on 2008-10-11
This message comes up when I run synaptic package manager




An error occured
The following details are provided:

E: dpkg was interrupted, yo must manually rub 'dpkg --configure -a' to correct the problem
E: _cache->open() failed, please report

---

### Post by yabbadabbadont on 2008-10-11
Try doing what it suggests to see if it will correct the problem.

Open a terminal window and run:
```
sudo dpkg --configure -a
```

Please post the output if it doesn't help.

---

