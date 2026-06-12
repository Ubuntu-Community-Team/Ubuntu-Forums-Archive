---
title: "FATAL: Module ndiswrapper not found"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by xboxbman on 2008-06-08
I'm trying to get my broadcom4328 wireless up and going on a fresh install of hoary, but I keep getting this error when I attempt
```
sudo modprobe ndiswrapper
```
I've done this no problem in all other releases, but not this time.  Any ideas?

---

### Post by django0909 on 2008-06-08
Try:

```
sudo apt-get install ndiswrapper-utils
```


and have another go...

A better point would be, why Hoary?

---

### Post by xboxbman on 2008-06-08
> **django0909 said:**
> Try:

```
sudo apt-get install ndiswrapper-utils
```


and have another go...

A better point would be, why Hoary?

i uninstalled it all then compiled from source, it works now.  Slight type on my part, I'm on Hardy, not hoary

---

