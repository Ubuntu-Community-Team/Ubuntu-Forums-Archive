---
title: "virtual box prob"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by intimatewipe on 2008-08-30
hello Peeps,trying to set up virtualbox but having some probs,first I installed from S.P.M ,(virtualbox-ose 86 virtualisation solution binaries).
when I try and set up my xp install I get the error in the pic,I cannot locate the recomended metapackage and when I try to download (my kernel version) using S.P.M it says I need the meta package which I cannot find,
bit of a noob so please if you can help (clearly) I would be very gratefull,
I also downloaded the Deb package from V.B site (for my type(amd64)) but it says something about some application cannot be used so go to sys/admin/and change something in preferences(can't remember now),tried this fix but the  lock thing in terminal stopped that,anyone know why that happens,I've seen that before,:confused:

---

### Post by benerivo on 2008-08-30
Tey removing the lock with```
sudo rm /var/lib/dpkg/lock
```Make sure you are not running any package management program when you do this.

---

