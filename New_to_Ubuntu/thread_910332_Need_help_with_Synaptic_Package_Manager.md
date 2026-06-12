---
title: "Need help with Synaptic Package Manager"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by DBLOK74 on 2008-09-04
Hello all I opened my Synaptic Package Manager and keep recieving  this error:   E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


Anyone know how to stop getting this error? Any help would be greatly appreciated.

Thanks in advance

<Sorry if posted in wrong section>

---

### Post by Perfect Storm on 2008-09-04
Close synaptic. Open the terminal and type (copy/paste);
```
sudo dpkg --configure -a
```

---

