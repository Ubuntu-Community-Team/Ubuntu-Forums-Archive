---
title: "Error to start updating"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by simorb01 on 2008-08-12
Hi all,

Can anyone help me?
I've got this message when I'm going to install the update:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What is this mean? How can I solve this problem?

Thanks

---

### Post by tuxxy on 2008-08-12
Type in this command

```
sudo dpkg --configure -a
```

---

### Post by simorb01 on 2008-08-12
> **tuxxy said:**
> Type in this command

```
sudo dpkg --configure -a
```


Thanks for your help :KS
It's working now..

---

