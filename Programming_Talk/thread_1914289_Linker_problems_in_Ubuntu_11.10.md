---
title: "Linker problems in Ubuntu 11.10"
date: 2012-01-24
forum: Programming Talk
---

### Post by cyberguijarro on 2012-01-24
Hi,

after upgrading to Ubuntu 11.10, I've found that many of my old and current developments can't be compiled anymore. I've reduced the problem to a simple example:

```

#include <X11/Xlib.h>

int main() {
    Display* display = XOpenDisplay(":0.0");
    XCloseDisplay(display);

    return 0;
}

```

Compiling it using:

```
g++ -lX11 test.cpp
```

or

```

g++ -c -o test.o test.cpp
g++ -lX11 -o test test.o

```

Causes a failure to happen:

```

/tmp/ccBAOpzy.o: In function `main':
test.cpp:(.text+0x11): undefined reference to `XOpenDisplay'
test.cpp:(.text+0x21): undefined reference to `XCloseDisplay'

```

---

### Post by cyberguijarro on 2012-01-24
Ok, looks like now (with GCC 4.6) parameter ordering is important:

```
g++ test.cpp -lX11
```

cuts it.

---

### Post by Arndt on 2012-01-24
> **cyberguijarro said:**
> Ok, looks like now (with GCC 4.6) parameter ordering is important:

```
g++ test.cpp -lX11
```

cuts it.

I didn't know the other form was possible.

---

