---
title: "XRaiseWindow / metacity / gnome wm programming"
date: 2009-06-15
forum: Programming Talk
---

### Post by mikio on 2009-06-15
dear forum,

i am trying to write a short C program to focus the 'next' window on the desktop - similarly to the default ALT-TAB functionality.

if discovered what i believe is the right X functions i need to call in order to do that. however, the code does not work (no error msg). 

here is the code i have written. if anyone could point out the problem with it, or point me in the right direction - that would be fantastic! many thanks, miki

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <X11/Xlib.h>
#include <X11/keysym.h>
#include <X11/extensions/XTest.h>


int main()
{
    Display *d = XOpenDisplay(NULL);
    int screen = DefaultScreen(d);
    XWindowAttributes attr;

    Atom atom;
    XEvent xev;
    Window w = RootWindow(d, screen);

    // get 'next' window, raise it and put focus on it (does not seem to work)
    XCirculateSubwindowsUp(d, w); 
    XRaiseWindow(d, w);
    XMapWindow(d, w);
    XSetInputFocus(d, w, RevertToParent, CurrentTime);
    
    //printf("\noverride: %d\n",attr.override_redirect );
    atom = XInternAtom (d, "_NET_ACTIVE_WINDOW", False);

    // try sending an event, so that metacity picks up what has been set on X before.. (does not seem to work)
    xev.xclient.type = ClientMessage;
	xev.xclient.serial = 0;
	xev.xclient.send_event = True;
	xev.xclient.display = d;
	xev.xclient.window = w;
	xev.xclient.message_type = atom;
	xev.xclient.format = 32;
	xev.xclient.data.l[0] = 2;
	xev.xclient.data.l[1] = 0;
	xev.xclient.data.l[2] = 0;
	xev.xclient.data.l[3] = 0;
	xev.xclient.data.l[4] = 0;

    XGetWindowAttributes(d, w, &attr);
    //attr.override_redirect = (gboolean)1;
    //XChangeWindowAttributes(d, w, 0, attr);

    XSendEvent (d,
          attr.root, False,
          SubstructureRedirectMask | SubstructureNotifyMask,
          &xev);

    XFlush(d); 
	XSync(d, False);
    XCloseDisplay(d);

    return(0);
}
```

---

### Post by gnagy on 2010-07-21
You need to move the call to XRaiseWindow to *after* XSendEvent.
The Window needs to be activated first, then you can raise it.

---

