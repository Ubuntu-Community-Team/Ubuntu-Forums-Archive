---
title: "Key Board buffer"
date: 2010-04-03
forum: Programming Talk
---

### Post by Vishnu V on 2010-04-03
Hi
    I am trying to make a virtual keyboard. For that i want to insert values to keyboard buffer .How can i insert value into keyboard buffer of Linux using  c/c++ or java

Thanks in advance
Have a nice day

---

### Post by heikaman on 2010-04-03
I don't think you can directly access the keyboard buffer, and don't think you should, however[COLOR="Navy"][/COLOR], you can use xlib to fake keyboard events, there's a good example [[COLOR="Blue"]**here**[/COLOR] ]("http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html")

you can also use the XTest extension and let it handle all the low-level XEvent setup for you, here's a quick example:

[PHP]  1 #include <X11/Xlib.h>
  2 #include <X11/keysym.h>
  3 #include <X11/extensions/XTest.h>
  4 
  5 int main(int argc, char **argv)
  6 {
  7     //open display
  8     Display *display = XOpenDisplay(NULL);
  9 
 10     //press and release
 11     XTestFakeKeyEvent(display, XKeysymToKeycode(display, XK_A), True, CurrentTime);
 12     XTestFakeKeyEvent(display, XKeysymToKeycode(display, XK_A), False, CurrentTime);
 13 
 14     //flush and close
 15     XFlush(display);
 16     XCloseDisplay(display);
 17     return 0;
 18 }
[/PHP]

compile:
[PHP]gcc xtest.c -o xtest -lXtst[/PHP]

dependencies:
[PHP]sudo apt-get install libxtst-dev[/PHP]

---

### Post by Vishnu V on 2010-04-04
Thank you very much .

---

