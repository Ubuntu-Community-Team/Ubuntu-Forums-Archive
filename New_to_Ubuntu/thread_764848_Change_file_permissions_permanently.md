---
title: "Change file permissions permanently"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by satterle on 2008-04-24
I have a config file for phpMyAdmin. It wants world write permissions disabled. The file is owned by root with read/write for group and others.

I sudo chmod the file permissions, but after I close phpMyAdmin they seem to revert to default because I am prompted to change the permissions again.

How can I change these permissions permanently?

---

### Post by ggaaron on 2008-05-06
And why do you need this? It is not secure, so probably phpMyAdmin changes permissions after exit so it would be secure.

---

### Post by satterle on 2008-05-09
because it's a localhost copy so there's no security issue. There was no issue until I upgraded to HH. Besides, the permission change is o-w (pMA wants no write permission on the config file) so being able to permanently change the permission IS the security fix!

---

