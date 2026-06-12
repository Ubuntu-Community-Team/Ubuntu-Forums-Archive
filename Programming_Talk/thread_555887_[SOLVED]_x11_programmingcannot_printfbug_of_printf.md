---
title: "[SOLVED] x11 programming::cannot printf::bug of printf&#65311;&#65311;"
date: 2007-09-20
forum: Programming Talk
---

### Post by fyplinux on 2007-09-20
Hi,

I am currently learning to program with the X11 lib, I met a problem that the printf function couldn't work until X11 is broken.


below is the code
================================

#include <X11/Xlib.h>
#include <stdio.h>
#include <stdlib.h>

int main(void){
	
  Display *d; int s; Window w; XEvent ev;
  int should_quit = 0;

  d = XOpenDisplay(NULL);
  s = XDefaultScreen(d);

  w = XCreateSimpleWindow(d, XRootWindow(d, s), 0, 0,
                          200, 200, 0,
                          XBlackPixel(d, s),
                          XWhitePixel(d, s));

  XSelectInput(d, w, ButtonPressMask);
  XMapWindow(d, w);

  **printf("dfdfdsfs");/*printf is called here*/**


  while(!should_quit)
    {
    XNextEvent(d, &ev);
    switch(ev.type)
        {
      case ButtonPress:
        should_quit = 1;
        break;
      default:
      break;
        }
    }

  return 0;
}


when I closed the window, the output of the terminal was
=============================
X connection to :0.0 broken (explicit kill or server shutdown).
dfdfdsfs


But, if the printf call is coded like:
printf("dfdfdsfs\n");

the program works properly, here is the output
==============================
dfdfdsfs
X connection to :0.0 broken (explicit kill or server shutdown).



The question is why printf cannot work properly without the newline endian?

thanks.

---

### Post by DMills on 2007-09-20
This is not an X11 question, but one of C...

Printf writes to the stdout stream, which by default is buffered[1], you can flush the buffer with fflush or by writing a newline (or you can set the stream to non buffered with the setvbuf call).

Regards, Dan.

[1]Line buffered if it is connected to a terminal, else just buffered, the line buffering is why \n works, and all buffers are flushed on exit which is why you see the first case.

---

### Post by gnusci on 2007-09-20
Yes thats right just try flushing the stdout as follow:


[B]printf("dfdfdsfs");/*printf is called here*/
fflush(stdout);[/B]

---

### Post by fyplinux on 2007-09-20
> **gnusci said:**
> Yes thats right just try flushing the stdout as follow:


[B]printf("dfdfdsfs");/*printf is called here*/
fflush(stdout);[/B]

yes, it works! 

Thank you.

---

