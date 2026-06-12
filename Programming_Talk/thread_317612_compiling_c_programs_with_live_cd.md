---
title: "compiling c programs with live cd"
date: 2006-12-12
forum: Programming Talk
---

### Post by vijayanand_sodadasi on 2006-12-12
Can I write programs (in C) and compile them with gcc on a system booted with live cd.  I tried doing this, but I got something like gcc not found.  I did a ```
dpkg -l|grep gcc
``` and found that gcc is present:confused: 

Do I need to install ubuntu on hard disk in order to write programs  and compile them.

Thanks,

---

### Post by hod139 on 2006-12-12
You need to install the package build-essential (which is available on the cd even if you don't have an internet connection),

---

