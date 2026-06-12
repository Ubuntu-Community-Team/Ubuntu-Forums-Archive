---
title: "Controlling mouse with Python in X"
date: 2008-07-08
forum: Programming Talk
---

### Post by nemtaro on 2008-07-08
Hi there,
I need to move the mouse cursor and generate mouse click events in X, and I'm hoping to use Python.

I understand that the standard Xlib library provides a XWarpPointer function which moves the cursor around. This works for me in C, but I can't seem to find the equivalent function in Python-xlib. Any suggestions would be appreciated :) 

Also, how would I go about creating a click event once I have the cursor in the right position?

Regards,
Nemtaro

---

### Post by pmasiar on 2008-07-08
at a glance, [http://x-python.sourceforge.net/Doc/x/index.html](http://x-python.sourceforge.net/Doc/x/index.html) does not mention XWarp (I know nothing about X windows, sorry). Did you tried to ask at x-python devel list? 

Another option will be to create custom wrapper for C functions you need.

---

### Post by nemtaro on 2008-07-08
Thanks for the reply. 
I'm relatively new to Python. By creating a custom wrapper, are you suggesting that I extend my Python code with the C function?

Where can I start reading about that?

This is the Xlib code which moves the cursor in C:
```

#include <X11/Xlib.h>
#include <X11/Xutil.h>

void mouseMove(int x, int y)
{
	Display *displayMain = XOpenDisplay(NULL);

	if(displayMain == NULL)
	{
		fprintf(stderr, "Error Opening the Display !!!\n");
		exit(EXIT_FAILURE);
	}

	XWarpPointer(displayMain, None, None, 0, 0, 0, 0, x, y);

	XCloseDisplay(displayMain);
}

```

Regards,
Nemtaro

---

### Post by pmasiar on 2008-07-08
Find Wybiral and msg him: he knows I think.

---

### Post by skeeterbug on 2008-07-08
> **nemtaro said:**
> Thanks for the reply. 
I'm relatively new to Python. By creating a custom wrapper, are you suggesting that I extend my Python code with the C function?

Where can I start reading about that?

This is the Xlib code which moves the cursor in C:
```

#include <X11/Xlib.h>
#include <X11/Xutil.h>

void mouseMove(int x, int y)
{
	Display *displayMain = XOpenDisplay(NULL);

	if(displayMain == NULL)
	{
		fprintf(stderr, "Error Opening the Display !!!\n");
		exit(EXIT_FAILURE);
	}

	XWarpPointer(displayMain, None, None, 0, 0, 0, 0, x, y);

	XCloseDisplay(displayMain);
}

```

Regards,
Nemtaro


Extending Python in C (provides a basic example): [http://docs.python.org/ext/ext.html](http://docs.python.org/ext/ext.html)

The entire API is here: [http://docs.python.org/api/api.html](http://docs.python.org/api/api.html)

---

### Post by nanotube on 2008-07-08
> **nemtaro said:**
> Hi there,
I need to move the mouse cursor and generate mouse click events in X, and I'm hoping to use Python.

I understand that the standard Xlib library provides a XWarpPointer function which moves the cursor around. This works for me in C, but I can't seem to find the equivalent function in Python-xlib. Any suggestions would be appreciated :) 

Also, how would I go about creating a click event once I have the cursor in the right position?

Regards,
Nemtaro

maybe this is what you are looking for? :
[http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html#SEC13](http://python-xlib.sourceforge.net/doc/html/python-xlib_14.html#SEC13)

---

### Post by nemtaro on 2008-07-11
Thanks to everyone for your replies, and Wybiral for his help.

I'm currently compiling the above mentioned C code into a share object, and importing it into Python:
```

// gcc mouse.c -Wall -c -fPIC -o mouse.o
// gcc mouse.o -lX11 -shared -Wl,-soname,mouse.so -o mouse.so

```

```

from ctypes import cdll, c_int

lib = "./mouse.so"

dll = cdll.LoadLibrary(lib)

mouseMove = (lambda x, y: dll.mouseMove(c_int(x), c_int(y)))

mouseMove(50, 50)

```

I'll report back if I manage to get the click events working. 

Cheers,
Nemtaro

---

### Post by pepijndevos on 2009-07-12
Any news on the click events?

I'm still searching for a pure python way to move and click the mouse. I already figured it out for Windows and Mac, Linux is the last missing part...

I'm writing a module to make life easy for the next one with our problems.
[http://www.python-forum.org/pythonforum/viewtopic.php?f=1&t=13825&start=0](http://www.python-forum.org/pythonforum/viewtopic.php?f=1&t=13825&start=0)
[http://code.google.com/p/pymouse/](http://code.google.com/p/pymouse/) (send me a PM for access)

---

### Post by unutbu on 2009-07-12
[http://plwm.sourceforge.net/](http://plwm.sourceforge.net/) is a window manager implemented in Python. If you run 
```

apt-get source python-plwm
```

you can take a look at its source code. Perhaps you'd find the answer there. (See [http://ubuntuforums.org/showpost.php?p=6760145&postcount=3](http://ubuntuforums.org/showpost.php?p=6760145&postcount=3))

Or, if we relax the "pure python" requirement, perhaps a simpler solution would be to study xdotool which is written in C. 
If you install the xdotool package, you can move the mouse with 
```

xdotool mousemove 850 70
```

and click with
```

xdotool  click 1
```

xdotool has less lines of code than plwm, so it might be easier to find exactly what you need there. 

Once you find the C code for clicking and moving the mouse, that code could be repackaged as a library with functions callable from Python. (See for example
[http://ubuntuforums.org/showpost.php?p=7249747&postcount=7](http://ubuntuforums.org/showpost.php?p=7249747&postcount=7))

---

### Post by DrMeers on 2010-01-13
> **nemtaro said:**
> Thanks to everyone for your replies, and Wybiral for his help.

I'm currently compiling the above mentioned C code into a share object, and importing it into Python:
```

// gcc mouse.c -Wall -c -fPIC -o mouse.o
// gcc mouse.o -lX11 -shared -Wl,-soname,mouse.so -o mouse.so

```

```

from ctypes import cdll, c_int

lib = "./mouse.so"

dll = cdll.LoadLibrary(lib)

mouseMove = (lambda x, y: dll.mouseMove(c_int(x), c_int(y)))

mouseMove(50, 50)

```

I'll report back if I manage to get the click events working. 

Cheers,
Nemtaro

A solution which avoids the C compilation step:

```
from ctypes import cdll

def move_mouse(x,y):
    dll = cdll.LoadLibrary('libX11.so')
    d = dll.XOpenDisplay(None)
    root = dll.XDefaultRootWindow(d)
    dll.XWarpPointer(d,None,root,0,0,0,0,x,y)
    dll.XCloseDisplay(d)
```

---

