---
title: "trobble updating"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Bigadada_saba on 2008-05-27
When i go to up date my laptop i get this error can someone help me with this.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by iaculallad on 2008-05-27
> **Bigadada_saba said:**
> When i go to up date my laptop i get this error can someone help me with this.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Issue the command on your terminal as it suggest.

Code:

```
sudo dpkg --configure -a
```

---

