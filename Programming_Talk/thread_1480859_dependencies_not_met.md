---
title: "dependencies not met"
date: 2010-05-12
forum: Programming Talk
---

### Post by jon zendatta on 2010-05-12
trying to fetch build-essential. How do I overcome this please

```

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages

```
:KS

---

### Post by jon zendatta on 2010-05-12
now i get this. HELP

```
@j-laptop:~$ sudo apt-get install g++-4.4 gcc-4.4 libstdc++6-4.4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-4.4 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  g++-4.4: Depends: gcc-4.4-base (= 4.4.3-3ubuntu3) but 4.4.3-4ubuntu5 is to be installed
           Depends: gcc-4.4 (= 4.4.3-3ubuntu3) but 4.4.3-4ubuntu5 is to be installed
  libstdc++6-4.4-dev: Depends: gcc-4.4-base (= 4.4.3-3ubuntu3) but 4.4.3-4ubuntu5 is to be installed
E: Broken packages

```:mad:

---

### Post by jon zendatta on 2010-05-12
no matter what way i try and install these packages i get dependencies not met & cannot go anywhere

---

### Post by MadCow108 on 2010-05-12
try apt-get install -f to fix the dependencies

---

### Post by jon zendatta on 2010-05-12
thanks mad cow
:KS

---

