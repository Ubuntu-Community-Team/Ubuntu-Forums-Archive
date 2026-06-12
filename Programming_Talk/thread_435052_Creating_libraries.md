---
title: "Creating libraries?"
date: 2007-05-06
forum: Programming Talk
---

### Post by Mathiasdm on 2007-05-06
I'm trying to find out more about writing libraries for usage by programs (both statical and dynamical ones). I've been looking around on google for a while, but it's a mess! I can't seem to find a clear explanation on writing libraries (I'm working in C and C++, by the way).

Could anyone point me to a nice link?

---

### Post by Wybiral on 2007-05-06
Look for the command "ar"
It's actually pretty simple (just compile some object files and pass them to ar)

For loading dynamic libraries, the "dlfcn.h" (link to it with "-ldl")
For compiling dynamic libraries (shared objects) use the "-fPIC" and "-shared" flags when generating the object files.

[http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html](http://www.yolinux.com/TUTORIALS/LibraryArchives-StaticAndDynamic.html)

---

