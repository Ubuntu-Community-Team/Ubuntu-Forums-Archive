---
title: "can't find my header files"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by skippylou on 2008-11-27
Hi, 
I have a new installation of ubuntu 8.04 x86_64.  I run make for a simple application. gcc gives lots of errors: cannot find stdio.h, stdlib.h, string.h &ct.  As these are standard C files I think it must me some kind of path problem. Cannot find any of these headers in the filesystem.  I have used C compilers for years but am absolutely new to ubuntu.  What is going on?  

Skippy

---

### Post by taurus on 2008-11-27
You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by skippylou on 2008-11-27
> **taurus said:**
> You need the build-essential package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install build-essential
```

Thanks, I am sure this would work, but the computer in question has no internet access until I compile and install wireless drivers. What exactly should I download?  When I get it on a DVD, what command to install it?

Skippy

---

### Post by taurus on 2008-11-27
The build-essential package should be on the install CD.  Make sure you have the CD enable in /etc/apt/sources.list, System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Then, you can install it with those two commands after you close down synaptic first or you can install it from synaptic.  Don't forget to click the Reload.

---

### Post by skippylou on 2008-11-27
> **taurus said:**
> The build-essential package should be on the install CD.  Make sure you have the CD enable in /etc/apt/sources.list, System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Then, you can install it with those two commands after you close down synaptic first or you can install it from synaptic.  Don't forget to click the Reload.

Thanks, Skippy

---

