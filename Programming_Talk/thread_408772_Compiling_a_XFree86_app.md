---
title: "Compiling a XFree86 app?"
date: 2007-04-13
forum: Programming Talk
---

### Post by duesen on 2007-04-13
Platform: Ubuntu 6.10, Gnome 2.16.1

I need to compile a C++ app which references XFree86 libraries (/usr/X11R6/lib):

#include "X11/Xlib.h"
#include "X11/keysym.h"
...

I noticed that Ubuntu came without these libraries, and heard that the system is based on xorg rather than xfree86.

Would appreciate any advice on how to either get XFree86 libs or maybe switch the app to use xorg libraries instead (where are those, by the way? I didn't see them either...)

Thanks!

---

### Post by WW on 2007-04-13
Install the package **libx11-dev**. You can use Synaptic, or in the terminal:
```

$ sudo apt-get install libx11-dev

```

---

