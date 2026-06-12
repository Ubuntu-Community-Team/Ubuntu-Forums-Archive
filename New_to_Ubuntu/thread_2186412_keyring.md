---
title: "keyring"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by ub9876 on 2013-11-07
xfce
 the keyring box CONSTANLY pops up and I want to get rid of it. The box asking for my password. How do I get rid of it.??thanks

---

### Post by philinux on 2013-11-07
> **ub9876 said:**
> xfce
 the keyring box CONSTANLY pops up and I want to get rid of it. The box asking for my password. How do I get rid of it.??thanks

In the past on my ubuntu install I usually delete this folder and it's contents and let the system rebuild it. Not sure if in same location for you.

```
/home/UserName/.local/share/keyrings
```

---

### Post by phyzik on 2013-11-07
You can go to Ubuntu Settings -> Passwords and Keys and check if you have more than one key owner. If you do, the easiest solution might actually be to delete all the keys, and start fresh after the restart...

---

