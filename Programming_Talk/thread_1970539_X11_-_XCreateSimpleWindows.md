---
title: "X11 - XCreateSimpleWindows"
date: 2012-05-01
forum: Programming Talk
---

### Post by andy100 on 2012-05-01
Hi, 
I am a beginner and I would try to work with X11 lib.
My first program is to create a windows, but despite I have copied the code from a manual I have several error in compilation phase.
Following you can see the code and the error (I use CodeBlock)

```

#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/Xos.h>
#include <X11/Xatom.h>
#include <X11/keysym.h>

//creating a Display pointer for the connection to the X server.
Display *dis;

//Create a variable to hold the window id.
Window win;

//create a window and map/display it on the screen.

int main() 
{
dis = XOpenDisplay(NULL);
win = XCreateSimpleWindow(dis, RootWindow(dis, 0), 1, 1, 500, 500, \
0, BlackPixel (dis, 0), BlackPixel(dis, 0));
XMapWindow(dis, win);
XFlush(dis);
/*Sleep 5 seconds before closing.*/
sleep(5);
return(0);
}

```
and the errors are:
undefined reference to XOpenDisplay
undefined reference to XCreateSimpleWindow
undefined reference to XMapWindow
undefined reference to XFlush

please could you help me?

---

### Post by DaviesX on 2012-05-01
I compiled it in command line, and the compilation is success but the linking part. 
```

davis@davis-PT20:~/Desktop$ gcc -c Test.c
davis@davis-PT20:~/Desktop$ gcc -o Test Test.o
Test.o: In function `main':
Test.c:(.text+0x12): undefined reference to `XOpenDisplay'
Test.c:(.text+0x82): undefined reference to `XCreateSimpleWindow'
Test.c:(.text+0x9e): undefined reference to `XMapWindow'
Test.c:(.text+0xab): undefined reference to `XFlush'
collect2: ld returned 1 exit status

```
So this means the static library missed. 
You have to use
```

#pragma comment ( lib, "library name" )

```
to include the implementation of those functions

---

### Post by DaviesX on 2012-05-01
Ok, problem solved :)

In command line, you might add an extra option -L /usr/X11R6/lib -lX11
```

gcc -O2 -o Test Test.c -L /usr/X11R6/lib -lX11

```

In CodeBlocks, 
Settings->Compiler and debugger->switch to linker settings->other linker options

then type in, 
-L /usr/X11R6/lib -lX11
press Ok, rebuild all->Run->XWindow come up ^_^

---

### Post by andy100 on 2012-05-02
Thank you Davies .. now it runs ...
but I'm very very surprise :( 
because in /usr I haven't X11R6 directory ....
could you explain this matter ...?

---

### Post by dwhitney67 on 2012-05-02
> **andy100 said:**
> Thank you Davies .. now it runs ...
but I'm very very surprise :( 
because in /usr I haven't X11R6 directory ....
could you explain this matter ...?

On many Linux systems, as it is on your system, the X11 header files are located in /usr/include/X11.  Since you specified the X11/ path with the header files in your code, it found them on your particular system -- there's no need to specify a -I compiler option.

However, if someone attempted to compile your code on a system where the same header files are found in /usr/include/X11R6, then they will not be as fortunate.  DaviesX has one those systems which required him to augment the compiler/linker command to indicate where to find the X11 (Revision 6) header files and library.

> 
My first program is to create a windows, but despite I have copied the code from a manual I have several error in compilation phase.

If your manual did not indicate how to compile/link an X11 program, then it is perhaps time that you seek another manual.

The only reason why you failed to reference the libraries in your first attempt is because you did not link against the X11 library.

---

