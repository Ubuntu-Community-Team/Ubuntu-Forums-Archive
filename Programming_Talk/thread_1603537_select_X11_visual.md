---
title: "select X11 visual ?"
date: 2010-10-22
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-22
After reading a [thread about tranparent windows]("http://ubuntuforums.org/showthread.php?t=1602571"), I'm trying to figure out how select the X11 visual that has alpha channel.
Following code shows there **is** one. I **can** use command line utility "transset" to make my window use it, so it is fully operational, but I just can't find the right function call in my own App :(

edit: code deleted... next post shows how to do it properly :)

---

### Post by worksofcraft on 2010-10-23
Meh... just incase anyone else wanted to know: solved it, but that was really confusing :confused:
[php]
// g++ xtran2.cpp -lX11 
#include <X11/Xlib.h> 
#include <X11/Xutil.h> // XVisualInfo 
#include <stdio.h> // printf 

int main(int Ac, char *Av[]) { 
	Display *display = XOpenDisplay(NULL); 
	if (!display) return fprintf(stderr, "Failed to open display\n"); 
    Screen *screen = DefaultScreenOfDisplay(display); 

	// find a visual with 32 bits and TrueColor
	XVisualInfo vinfo;
	if (!XMatchVisualInfo(
		display, XDefaultScreen(display), 32, TrueColor, &vinfo)
	) return fprintf(stderr, "no 32 bit visual\n");
	const char *vic_name[] = {
		"StaticGray", "GrayScale", "StaticColor",
		"PseudoColor", "TrueColor", "DirectColor"
	};
 	printf("Using visual= %ld, class=%s, depth=%d\n",
         vinfo.visualid,
         vic_name[vinfo.c_class],
         vinfo.depth
	);

	// identify top level window
	Window root_window = XDefaultRootWindow(display);

	long black = BlackPixelOfScreen(screen); 
	long white = WhitePixelOfScreen(screen);
	const long translucent = 0x80<<24; 
 	XSetWindowAttributes attrs;
	attrs.colormap = XCreateColormap(
		display, root_window, vinfo.visual, AllocNone
	);
	attrs.background_pixel = black | translucent;
	attrs.border_pixel = white | translucent;

	const int window_width = 200; 
	const int window_height= 150; 
	const int border_width = 19;

	Window my_window = XCreateWindow(
		display, root_window, 0, 0, window_width, window_height,
		border_width, vinfo.depth, InputOutput,
		vinfo.visual, CWBackPixel | CWColormap | CWBorderPixel, &attrs
	);
	XMapRaised(display, my_window); // display it 

	// look for some user input
	long eventMask = StructureNotifyMask|KeyPressMask|KeyReleaseMask; 
	XSelectInput( display, my_window, eventMask ); 
	// also register interest delete window message with the window manager 
	Atom wmDeleteMessage = XInternAtom(display, "WM_DELETE_WINDOW", False); 
	XSetWMProtocols(display, my_window, &wmDeleteMessage, 1); 

	XEvent evt; 
	bool loop = true; 
	while (loop) { 
		// Send (flush) all requests and wait for an event 
		XNextEvent( display, &evt ); 
		printf("event type=%d\n", evt.type); 
		switch (evt.type) { 
		case ClientMessage: 
			printf("ClientMessage event\n"); 
			loop = !(evt.xclient.data.l[0] == wmDeleteMessage); 
			break; 
		default: break; 
		} 
	}

	XCloseDisplay(display);
	return !printf("exits normally\n"); 
} 
[/php]

I'm not sure how portable that is.. I only tested with 64 bit g++ compile and I'm sure it will fail if you haven't got an alpha channel enabled visual, although hopefully it will tell you that ;)

---

### Post by worksofcraft on 2010-10-23
actually no.. I'm still confused :confused:
Half the border is translucent no matter what I set and white backgrounds are never translucent and when I set the alpha channel to opaque things are still translucent... and... oh well, I didn't really need it :P

---

