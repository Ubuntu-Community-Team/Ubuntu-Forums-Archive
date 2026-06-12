---
title: "fdisk source"
date: 2010-03-12
forum: Packaging and Compiling Programs
---

### Post by drave on 2010-03-12
where is it ?

"apt-get source fdisk" gives  
E: Unable to find a source package for fdisk

in fact there doesnt appear to be an fdisk package at all.
there's gnu_fdisk, but according to aptitude its not that one thats installed. hmm. duhh!!

thanks

---

### Post by sisco311 on 2010-03-12
fdisk is provided by the util-linux package:
```
whereis fdisk
dpkg -S /sbin/fdisk

```;)

---

### Post by drave on 2010-03-12
thanks

---

