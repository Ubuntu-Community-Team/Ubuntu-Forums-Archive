---
title: "Why do Ubuntu deb packages depend on windows.h?"
date: 2017-08-05
forum: Programming Talk
---

### Post by carson.mcneil on 2017-08-05
I installed wglew.h via ```
sudo apt-get install libglew-dev
```. When I try to build packages using it I get the following error:
```
/usr/include/GL/wglew.h:70:21: fatal error: windows.h: No such file or directory
 #include <windows.h>

```
Why does an Ubuntu package depend on windows.h? I was under the impression that this header was Windows only?

---

### Post by TheFu on 2017-08-05
There are lots of cross-platform programs.  Usually, for C/C++ programs, the Makefile would set some variables to ensure the correct platform options, macros, environment, libs are used.  The makefile should have some sort of configure or readme that explains how to compile for each different platform.

OTOH, I don't know anything specific about this package.  A quick google for that header found the file ... the area inside it ... seems there's a WINAPI that is being set on your system that shouldn't.


```
#if !defined(WINAPI)
#  ifndef WIN32_LEAN_AND_MEAN
#    define WIN32_LEAN_AND_MEAN 1
#  endif
#include <windows.h>
#  undef WIN32_LEAN_AND_MEAN
#endif
```

So ... check the makefile, install, readme.

---

