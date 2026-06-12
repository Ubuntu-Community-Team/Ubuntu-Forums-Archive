---
title: "[SOLVED] How to install debhelper on gutsy?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by kevinlang21 on 2008-06-17
It seems to me that it should already be installed, but here's my input and output:

> kevin@computer:~$ sudo apt-get install debhelper 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate

Thanks for your help.

---

### Post by wolfen69 on 2008-06-17
i just did 
```
sudo apt-get install debhelper -s
``` (fake install) and had no problem "installing it". perhaps it's because of the medibuntu repos or 3rd party repos. if you dont have them, i suggest getting them. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by kevinlang21 on 2008-06-18
it was off of a fresh install, and after i installed updates, i tried again and it worked without problem. thank you anyways!

---

