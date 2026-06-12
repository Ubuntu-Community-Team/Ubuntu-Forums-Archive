---
title: "ndas-admin error"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by garrethdk on 2008-09-22
i screwed up on installing ndas-admin ages ago now every time i'm installing something i get the following error

Setting up ndas-admin (1.0.2-24) ...
update-rc.d: /etc/init.d/ndas: file does not exist
/bin/sh: Can't open /etc/init.d/ndas
dpkg: error processing ndas-admin (--configure):

can someone tell me now to get rid of this please ?
also is there any link to give me the basics of when software is installed where it goes ?

cheers

---

### Post by cariboo on 2008-09-22
Go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

Jim

---

### Post by spiderbatdad on 2008-09-22
```
sudo dpkg --configure -a
```

---

### Post by garrethdk on 2008-09-23
none of these work still get the same error message , this i might have to do a rebuild

---

