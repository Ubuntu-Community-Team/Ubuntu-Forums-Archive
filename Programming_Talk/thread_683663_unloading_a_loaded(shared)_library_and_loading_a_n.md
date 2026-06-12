---
title: "unloading a loaded(shared) library and loading a new one"
date: 2008-01-31
forum: Programming Talk
---

### Post by SandyKhan on 2008-01-31
i have created symbolic links to point to some shared libraries. During the execution of my program, i want those symbolic links to point to some other libraries. (Note: I can't do it at the start, as the firstly pointed libraries are necessary to start the execution).

when i delete a symbolic link, and try to create a new link pointing to another library, the execution hangs. plz guide me how to do this.

i faced this problem when i deleted the symbolic link **libpthread.so.0** pointing to **libpthread-0.9.29.so**, and tried to create new symbolic link with the same name pointing to **libpthread-0.9.27.so**

---

### Post by stroyan on 2008-01-31
Are you sure you want to change the symbolic links?  It seems very disruptive.
You can effect which shared libraries are used by setting the LD_LIBRARY_PATH environment variable.
That will only affect specific processes that inherit the environment variable setting.
You can see documentation of LD_LIBRARY_PATH and other options with "man ld.so".

---

### Post by lnostdal on 2008-01-31
i believe what you're after is described in the dlopen and dlclose man-pages

but messing with this in context with threads .. where you might, at any time(?), still have a thread of execution running "based on" the old library .. i don't know .. threads can be messy enough as they are IMHO x)

---

