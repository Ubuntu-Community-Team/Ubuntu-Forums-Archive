---
title: "help needed in mouse displacement measurement program"
date: 2009-05-09
forum: Programming Talk
---

### Post by montamer on 2009-05-09
Hi
Im trying to write a program which outputs the distance the mouse travelled and in what direction.
I dont know whr to start, can someone give a hint or a program which does this?
-Thanx

---

### Post by montamer on 2009-05-09
one thing im thinking is use
popen("cat /dev/input/mice","r")
and read the data coming from the device.

But when i type 
"sudo cat /dev/input/mice" I get the output; but i cant tell wht the output is exactly to interprete in the program.

---

### Post by crazyfuturamanoob on 2009-05-09
Maybe get the cursor position directly from X11? You didn't say which language you use so I assume it's C.

```

#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h>
#include <assert.h>

int main (void)
{
   Display *dpy;
   Window root, child;
   int rootX, rootY, winX, winY;
   unsigned int mask;

   dpy = XOpenDisplay(NULL);
   assert(dpy);

   while (1) {
     XQueryPointer(dpy,DefaultRootWindow(dpy),&root,&child,&rootX,&rootY,&winX,&winY,&mask); 
     printf("x=%d - y=%d\n", rootX, rootY);
     /*sleep(1);*/
   }
}

```

(remember to add -lX11 when compiling)

---

### Post by AlecSchueler on 2009-05-09
> **crazyfuturamanoob said:**
> ...You didn't say which language you use so I assume it's C...
The example ("popen('cat /dev/input/mice','r')") looks like Python.

---

### Post by Arndt on 2009-05-09
> **montamer said:**
> one thing im thinking is use
popen("cat /dev/input/mice","r")
and read the data coming from the device.

But when i type 
"sudo cat /dev/input/mice" I get the output; but i cant tell wht the output is exactly to interprete in the program.

I found these two sites which seem useful: [http://kerneltrap.org/node/6786](http://kerneltrap.org/node/6786) and [http://www.computer-engineering.org/ps2mouse/](http://www.computer-engineering.org/ps2mouse/).

---

### Post by crazyfuturamanoob on 2009-05-10
Make a C function which returns mouse coordinates and compile it as Python module?

---

### Post by crazyfuturamanoob on 2009-05-10
I read the python docs and made you a module which does this. Simply run "python setup.py build" to compile it. Then put the output .so file in same directory with your python program.

Usage:
```

import xmouse

while (1):
    coords = xmouse.get_pos()
    print str(coords)

```


Edit: there is also a Python implementation of Xlib so it's possible to do this without a C module.

---

