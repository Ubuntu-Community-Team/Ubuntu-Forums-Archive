---
title: "xpeekevent not working"
date: 2009-05-23
forum: Programming Talk
---

### Post by Bucky24 on 2009-05-23
I am trying to write a simple C program that uses XLibs to log key events on my computer (this is not for any illegal means-I am trying to write a program that does certain things when I hit keys, but does not necessarily have to be in focus).

This is the code I am using:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#include <unistd.h>

#include <X11/Xlib.h>
#include <X11/Xutil.h>


int main(int argc, char **argv) {
	char *display_name = getenv("DISPLAY");
    	Display *display = XOpenDisplay(display_name);
	if (display == NULL) printf("bad");
	XEvent *event;
	XPeekEvent(display,event);
	printf("type: %d\n",event->type);
	if (event->type == KeyReleaseMask) {
		printf("%d\n",event->xkey.keycode);
	}
	XCloseDisplay(display);
	return 0;
}

```

However all this program does is enter an infinite loop (meaning that xpeekevent is finding nothing). I feel there is something missing, but there is precious little information on the web about how to use this function properly. How might I get this program to work?

Thank you for your time.

-Bucky24

---

### Post by cdekter on 2009-05-23
Unfortunately what you are attempting to do is not possible using this approach. The only time an X client can receive events is when it has the focus. You'd have to create a window and instruct the server to send you key events (by setting the appropriate mask), however as soon as the window lost focus your program would stop receiving events.

There are several ways that do work, but they are not simple. 
[LIST]
[*]The Record extension (an X Server extension), but this is currently broken as of Jaunty. 
[*]Gnome's AT-SPI (which only works with GDK-based applications). 
[*]Read directly from the X server event devices exposed under /dev/input (for this your application requires root privileges)
[/LIST]

If you're interested in more information, and know a bit of Python, you can check out the source of my application AutoKey ([http://sourceforge.net/projects/autokey](http://sourceforge.net/projects/autokey)). I think you might find it does what you are trying to achieve, or at the very least the source code will give you some ideas.

---

### Post by Bucky24 on 2009-05-23
I will look into these. Thank you for your help.

-Bucky24

---

