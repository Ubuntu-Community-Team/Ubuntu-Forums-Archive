---
title: "g++ can't find standard library"
date: 2016-08-06
forum: Programming Talk
---

### Post by cameron24 on 2016-08-06
Hi, I'm trying to start learning c++, and I've been trying to compile Hello, World using g++. The compiler gets tripped up at ```
#include "std_lib_facilities.h"
```, because it doesn't know where that is. It returns an error message saying > fatal error: std_lib_facilities.h: No such file or directory. How do I tell the compiler where to find the library from the header? For that matter, where *are *the standard libraries, assuming they're already on my computer somewhere?

Thanks for your help!

---

### Post by spjackson on 2016-08-07
std_lib_facilities.h is not a standard header. You need to create it yourself or download it. See [http://www.stroustrup.com/Programming/](http://www.stroustrup.com/Programming/) and [http://www.stroustrup.com/Programming/std_lib_facilities.h](http://www.stroustrup.com/Programming/std_lib_facilities.h)

Genuine standard headers are found automatically; you do not need to do anything.

---

### Post by cameron24 on 2016-08-07
Ok, that makes sense, thanks a lot!

Follow-up question: once I download the header, does it matter where I save it, or will the compiler be able to find it automatically as long as it is saved somewhere under the right name?

---

### Post by Rocket2DMn on 2016-08-07
It needs to be in the same directory, unless you specify the -I (upper case i) flag followed by the directory location of the header file.  For example:
```

g++ -I /path/to/header/dir <source_files>

```

---

### Post by dwhitney67 on 2016-08-07
My $0.02.... don't use std_lib_facilities.h.  It is not a standard header file, and thus you will not find it on any computer (unless you install it yourself).

Why not open up the file to see what 'facilities' are truly being provided.  This might shed illumination into which actual standard headers files are being used (and needed) by your application.

---

