---
title: "Can't Remove gISOmount"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Wiking on 2012-01-08
I tried to uninstall Gisomount in the Muon sofware center, but I get a message that another package is using it.

How can I remove this program?

Thanks.

> Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove any packages.

---

### Post by Wiking on 2012-01-08
Fixed it, typed in: 

```
sudo fuser -vki
/var/lib/dpkg/lock;sudo dpkg --configure -a
```

It seems Muon was locked in.

---

### Post by halitech on 2012-01-08
glad  to hear you were able to figure it out and thanks for posting what you did to resolve the issue :(

---

