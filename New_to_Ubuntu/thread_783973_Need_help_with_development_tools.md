---
title: "Need help with development tools"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by rmyrick on 2008-05-06
I'm new to this forum activity, but I used Red Hat 9.0 several years ago off and on. Since it is no longer supported, and I can't (won't) pay for Red Hat Enterprise, I decided to migrate to Ubuntu. However, I'm having a problem here. 

I can't seem to compile even the simplest C++ programs using "gcc" in the Gnome terminal (the terminal seems to be fine); I get an error message that "cc1plus" is not found. Also, I would like to obtain "flex" and "bison" which always shipped with and were installed properly with RH. I did notice that several other tools that I find useful, such as dc, bc and the core utilities are fine, but "gcc", "flex" and "bison" is a must for me.  :confused:

---

### Post by pro003 on 2008-05-06
try to search those tools through Synaptic (System > Administration > Synaptic)... probably they are third party software so you will have to enable repositories...

---

### Post by Cypher on 2008-05-06
If you install the Desktop version of Ubuntu, the build environment isn't installed automatically for you. But you can install it with
```

sudo apt-get install build-essential bison flex

```

---

