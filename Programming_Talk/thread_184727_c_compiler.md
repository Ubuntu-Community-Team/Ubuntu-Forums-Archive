---
title: "c compiler"
date: 2006-05-30
forum: Programming Talk
---

### Post by saif76 on 2006-05-30
hi
can any one tell me how to use the c compiler in ubuntu unix.
i have used red hat linux , in that for compiling a c program all i have to do is use the command " $ cc sample.c " , but when i use this in ubuntu i get and error saying no command cc exists . pls help

---

### Post by bruce89 on 2006-05-30
```
sudo apt-get install build-essential
```

---

### Post by nanotube on 2006-05-30
and just to explain further, that build-essential package will install a bunch of software building tools, the compiler among them.

---

### Post by thumper on 2006-05-30
**cc** then exists as a symlink to **gcc**

---

