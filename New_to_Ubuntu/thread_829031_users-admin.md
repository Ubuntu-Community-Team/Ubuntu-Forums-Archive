---
title: "users-admin"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by seyiisq on 2008-06-14
I did a silly thing, i reconfigure my default user ( The one i created during setup) by removing the "Administer this system" property. now i can't log in as root nor can i even unchange it.

---

### Post by aysiu on 2008-06-14
Reboot into recovery mode and ```
adduser *username* admin
```

More details here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

