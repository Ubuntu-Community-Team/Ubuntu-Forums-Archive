---
title: "XIO: fatal IO error 11 (Resource temporarily unavailable)"
date: 2010-07-22
forum: Programming Talk
---

### Post by nmccrina on 2010-07-22
I'm writing a simple Xlib program, and have a bit of a problem. The program is supposed to display a window, then wait for the user to kill it with the "x" button. It works, but each time the window closes I get the error
```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 12 requests (10 known processed) with 0 events remaining.

```

Here is the program:
```
#include <X11/Xlib.h>
#include <iostream>

int main()
{
	Display* dpy;
	
	dpy = XOpenDisplay(NULL);
	
	std::cout << std::endl;
	
	if (dpy == NULL)
	{
		std::cout << "Error: could not open display";
		return 0;
	}
	else
	{
		std::cout << "Success!";
	}
	
	int blackColor = BlackPixel(dpy, DefaultScreen(dpy));
	int whiteColor = WhitePixel(dpy, DefaultScreen(dpy));
	
	Window w = XCreateSimpleWindow(dpy, DefaultRootWindow(dpy), 0, 0,
		200, 100, 0, whiteColor, blackColor);
	
	XSelectInput(dpy, w, StructureNotifyMask);
	
	XMapWindow(dpy, w);
	
	GC gc = XCreateGC(dpy, w, 0, NULL);
	
	XSetForeground(dpy, gc, whiteColor);
	
	// Wait for window to be mapped
	while(true)
	{
		XEvent e;
		XNextEvent(dpy, &e);
		if (e.type == MapNotify)
		{
			break;
		}
	}
	
	XDrawLine(dpy, w, gc, 10, 60, 10, 0);
	XFlush(dpy);
	
	// Wait for destroy event
	while(true)
	{
		XEvent e;
		XNextEvent(dpy, &e);
		if (e.type == DestroyNotify)
		{
			break;
		}
	}
	
	std::cout << std::endl << std::endl;
	return 0;
}
```

I googled it, but it seemed the most common reply was just to ignore it, since it doesn't actually affect the program. I would prefer knowing what's causing it, though.

---

