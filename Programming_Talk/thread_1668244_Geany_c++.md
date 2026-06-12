---
title: "Geany c++"
date: 2011-01-16
forum: Programming Talk
---

### Post by sino93 on 2011-01-16
I am using Geaney as UI for c++ programming and i'm tring to use X but it gaves me this errors.

> g++ -Wall -o "x_test" "x_test.cpp" (in directory: /home/alex/c++)
Compilation failed.
/tmp/ccy6bthM.o: In function `main':
x_test.cpp:(.text+0x32): undefined reference to `XOpenDisplay'
x_test.cpp:(.text+0x14c): undefined reference to `XCreateSimpleWindow'
x_test.cpp:(.text+0x172): undefined reference to `XSelectInput'
x_test.cpp:(.text+0x18a): undefined reference to `XMapWindow'
x_test.cpp:(.text+0x19f): undefined reference to `XNextEvent'
x_test.cpp:(.text+0x200): undefined reference to `XCloseDisplay'
collect2: ld returned 1 exit status


---

### Post by worksofcraft on 2011-01-16
in your source file you must specify:
```

#include <X11/Xlib.h>

```

on the compile command line you need to specify -lX11

(Just to avoid confusion, note that is letter lower case l for "library" followed by uppercase X and the number 11)

---

### Post by sino93 on 2011-01-16
I already included that. I forgot to say, it shows teh eror when i build. I added that option to the compiler but it has the same result, maybe i dit it wrong.

Nvm, it worked eventually, i changed the order of the options while compiling.
> g++ -lX11 -Wall -o "x_test" "x_test.cpp"

Thanks a lot.

---

### Post by dwhitney67 on 2011-01-16
Nevermind.

--------------------

Why do you place quotes around your filenames in the g++ statement?  Try
```

g++ -Wall -o x_test x_test.cpp -lX11

```
If this still does not work, then the only thing I can assume is that you have not installed in the X11 development library.

I tested the program below on my system, and it compiled/linked just fine:
```

#include <X11/Xlib.h>

int main()
{
   Display* display = XOpenDisplay(":0");

   XCloseDisplay(display);
}

```

---

### Post by worksofcraft on 2011-01-16
> **sino93 said:**
> ...
Nvm, it worked eventually, i changed the order of the options while compiling.


Thanks a lot.

YW... and remember to use thread tools for marking your threads as "solved" when it has been solved ;)

---

