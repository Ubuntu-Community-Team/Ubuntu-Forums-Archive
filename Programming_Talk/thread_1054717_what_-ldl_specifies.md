---
title: "what -ldl specifies?"
date: 2009-01-30
forum: Programming Talk
---

### Post by void_void on 2009-01-30
i have to give '-ldl' switch to gcc but i don't know what it specifies...
any one of you pls tell me googling doesn't work here. . .

---

### Post by MeduZa on 2009-01-30
> **void_void said:**
> i have to give '-ldl' switch to gcc but i don't know what it specifies...
any one of you pls tell me googling doesn't work here. . .

if you use dynamic libraries with for example dlfcn.h (dlopen, dlsym, etc) you need to use -ldl in the linker line.

---

### Post by snova on 2009-01-30
It tells the linker to link the **dl** library, which is located at /usr/lib/libdl.so. -l is the switch to add a library, dl is the name of it (without the lib prefix or .so extension).

This library includes functions for dynamically loading shared libraries.

---

