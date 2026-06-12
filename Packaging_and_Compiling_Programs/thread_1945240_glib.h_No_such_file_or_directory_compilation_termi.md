---
title: "glib.h: No such file or directory compilation terminated."
date: 2012-03-22
forum: Packaging and Compiling Programs
---

### Post by kahgfakhjsf on 2012-03-22
I'm trying to compile a C source code file with gcc. 

The file includes glib.h
```
#include <glib.h>
```And, when compiling: 
> gps_example.c:1:18: fatal error: glib.h: No such file or directory
compilation terminated.I do, however, have glib.h in my system. Running find /usr -iname glib.h returns:
> /usr/include/glib-2.0/glib.hMy system has glib.h, but for some reason my system doesn't think it has the .h file. How can I tell it where glib.h is?

---

### Post by Bachstelze on 2012-03-22
You need to add the output of

```
pkg-config --cflags glib-2.0
```

to your compiler flags.

---

