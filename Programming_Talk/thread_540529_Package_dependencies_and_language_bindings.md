---
title: "Package dependencies and language bindings"
date: 2007-09-01
forum: Programming Talk
---

### Post by code-breaker on 2007-09-01
I have written a program in python, and I'm working on a deb package for it. My program depends on libaudiere-1.9.4 (it is an audio player), but it seems to me that the libaudiere package does not include python bindings (I think I remember building the whole package from source, python bindings included). So simply depending on libaudiere isn't enough. How do I properly handle this dependency?

---

### Post by Game_Ender on 2007-09-02
Create another package which has the python bindings.  That pretty much the standard debian way.  Then just depend on that package.

---

