---
title: "install java problem"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by bayarja on 2008-05-08
hi all again. i search for java in add/remove. then look that error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by kpkeerthi on 2008-05-08
Close Add/Remove programs and Synaptic if they are open and run this command in a terminal window
```
sudo dpkg --configure -a
```
It should clear things up.

---

### Post by bayarja on 2008-05-08
> **kpkeerthi said:**
> Close Add/Remove programs and Synaptic if they are open and run this command in a terminal window
```
sudo dpkg --configure -a
```
It should clear things up.

Thanks a lot. 


All Best Regards
Bayarjaa

---

### Post by Zeck on 2008-05-08
> **bayarja said:**
> Thanks a lot. 


All Best Regards
Bayarjaa

Gutsaad bai Bayarjaa guai.

---

