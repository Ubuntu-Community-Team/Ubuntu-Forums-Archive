---
title: "error message: E: dpkg was interrupted,"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by rm2011 on 2008-08-24
Hi,
I am just starting with ubuntu Hardy.  It says  there are 84 updates available, so i try to install them.  When i try to install them i get this error message:  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


I tried opening terminal and running this, but it says "dpkg requires superuser privilege.  I dont now what this means, and can not figue out where to go from here.  :confused:

---

### Post by Barrucadu on 2008-08-24
Prefix the command with sudo:
```
sudo dpkg --configure -a
```

You will need to type your password. It won't show on the screen, but it is being entered. Just type it and press enter when done.

---

### Post by Ryadt on 2008-08-24
> **rm2011 said:**
> Hi,
I am just starting with ubuntu Hardy.  It says  there are 84 updates available, so i try to install them.  When i try to install them i get this error message:  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report


I tried opening terminal and running this, but it says "dpkg requires superuser privilege.  I dont now what this means, and can not figue out where to go from here.  :confused:

Do in terminal```
sudo dpkg --configure -a
```

---

### Post by Kevbert on 2008-08-24
What you need to do in terminal is use
```
sudo dpkg --configure -a
```
in terminal.  While you're at it use
```
sudo apt-get install -f
```
to repair any damaged packages as well as
```
sudo apt-get update

```

---

### Post by aysiu on 2008-08-24
Or, instead of typing the command, you can also copy and paste it.

---

