---
title: "Shared libraries"
date: 2008-09-15
forum: Programming Talk
---

### Post by Emill on 2008-09-15
Hello. I have made an application with libglademm-2.4. I can run it on my computer. The problem is that I want it to run on computers that don't have libglademm-2.4 installed and don't have root access. Either by including the hole glade-thing in my binary file, or having some .so-files beside it or something else. But I don't know how to do it...

---

### Post by dribeas on 2008-09-15
> **Emill said:**
> Hello. I have made an application with libglademm-2.4. I can run it on my computer. The problem is that I want it to run on computers that don't have libglademm-2.4 installed and don't have root access. Either by including the hole glade-thing in my binary file, or having some .so-files beside it or something else. But I don't know how to do it...

You can go different ways here. First would be statically link the lib, I don't usually do it, and when I do is through CMake, so I cannot really help there. Then you can dynamically link it and provide the library in a package, in that case, you might need to change LD_LIBRARY_PATH environment variable to point to the directory in which you have placed all .so files (libglademm-2.4.so).

---

### Post by nvteighen on 2008-09-15
A third solution (besides static linking and dynamic linking) is dynamic loading (you load the library at execution time). Though that's usually meant for plugin support, maybe it could cover you needs (it will certainly be an uncommon approach, but who cares?).

1. You place the libraries where you like.
2. Include dlfcn.h (I suppose cdlfcn in C++)
3. Learn how to use dlopen(), dlsym() and friends. They usually involve giving some path to where the library to be loaded at run-time is placed.
4. Link your application to libdl.so (the dynamic loader library) with -ldl switch. You can play it safe by assuming that the library is installed in any regular GNU/Linux system.

---

