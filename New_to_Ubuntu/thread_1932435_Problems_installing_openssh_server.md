---
title: "Problems installing openssh server"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by thatsportsfan on 2012-02-27
I installed ubuntu server and I wanted to download a ssh server to get access to it from my laptop but I get the following below. 

When I try to sudo apt-get install openssh-server I get - 
"Package openssh-server is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
 E: Package openssh-server has no installation candidate."

Any help would be appreciated.

---

### Post by josephmills on 2012-02-27
> **thatsportsfan said:**
> I installed ubuntu server and I wanted to download a ssh server to get access to it from my laptop but I get the following below. 

When I try to sudo apt-get install openssh-server I get - 
"Package openssh-server is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
 E: Package openssh-server has no installation candidate."

Any help would be appreciated.
try 
```
sudo apt-get install ssh openssh-server
```
hope that this helps

---

### Post by CharlesA on 2012-02-27
If that doesn't work, try updating the package lists and try installing it again.

```
sudo apt-get update
```

---

### Post by thatsportsfan on 2012-02-27
Thanks that worked!

---

### Post by josephmills on 2012-02-27
that is Great news then! Do you think that you could mark this as being solved ?

---

