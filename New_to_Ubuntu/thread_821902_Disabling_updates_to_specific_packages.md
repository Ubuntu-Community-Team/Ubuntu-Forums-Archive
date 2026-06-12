---
title: "Disabling updates to specific packages"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by tyguy2259 on 2008-06-07
Is it possible to disable a specific package from updating in the Update Manager and through apt-get?

---

### Post by rampageoberon on 2008-06-07
Yes it is. Have a read through the man pages.

```
man apt-get
```

---

### Post by sdennie on 2008-06-07
You should be able to this in synaptic by selecting the package(s) and using Package->Lock Version.

---

### Post by Oldsoldier2003 on 2008-06-07
> **vor said:**
> You should be able to this in synaptic by selecting the package(s) and using Package->Lock Version.

once you do that its also a good idea to

```
 sudo ln -fs /var/lib/synaptic/preferences /etc/apt/preferences
```
this ensures synaptic and apt-get respect the same locks
bug in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178)

---

