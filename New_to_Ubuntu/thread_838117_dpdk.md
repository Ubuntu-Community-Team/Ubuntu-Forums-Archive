---
title: "dpdk"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by sahajoda on 2008-06-23
Having trouble updating through Update Manager and Synaptic Package Manager.
keeps telling me:
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report[/B]. 

what to do???

---

### Post by rraj.be on 2008-06-23
Just run this in terminal

```
sudo dpkg --configure -a
```
To open terminal go to 

Applications --> Acessories -->Terminal

---

### Post by sahajoda on 2008-06-23
Thanks worked like a charm.....:guitar:

---

