---
title: "checking for necessary dependencies"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2013-08-30
Hi All

I have installed Freespeak, and it just wont work. I installed it with software center, uninstalled it, installed it with synaptic, reinstalled it with synaptic. No joy. Program runs, just wont translate.

My question is, how can I check that the necessary dependancies are installed? Could a missing depedancy cause this? I would think that installing it via synaptic and software center, that they would know what dependancies are necessary and install them automatically.

I don't know what to think. 

Any thoughts?

Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-53-generic-pae
GNOME 3.4.2

---

### Post by newb85 on 2013-08-30
If you installed the version in the repository (as apposed to downloading with your internet browser or something), then yes, Software Center, Synaptic, and apt-get should all install the necessary dependencies automatically.

The package didn't get great ratings, but I don't see any reviews that say it doesn't work.

If you want to manually check the dependencies, in a terminal, type

```
apt-cache showpkg freespeak
```

The description includes listed dependencies.

---

