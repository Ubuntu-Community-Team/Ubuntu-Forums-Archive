---
title: "Opening a new tab in Gnome-Terminal command line program"
date: 2012-02-19
forum: Programming Talk
---

### Post by sushemsu on 2012-02-19
The situation - I wanted to have gnome-terminal open a net tab in the current terminal window but didn't have the ability to use the xdotool.

I browsed a few really interesting posts and ended up converting 
[http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html](http://www.doctort.org/adam/nerd-notes/x11-fake-keypress-event.html)
into my code of 
```
#include <X11/Xlib.h>
#include <X11/keysym.h>
#include <stdio.h>
#define KEYCODE1 XK_Shift_L
#define KEYCODE2 XK_Control_L
#define KEYCODE3 XK_t
// compile with g++ -o appname sourcename.cpp -lX11
XKeyEvent event;
XKeyEvent createKeyEvent(Display *display, Window &win, Window &winRoot, int keycode, int modifiers)
{
event.display = display;
event.window = win;
event.root = winRoot;
event.x = 1;
event.y = 1;
event.same_screen = True;
event.type = KeyPress;
return event;
}
main()
{
Display *display = XOpenDisplay(0);
if (display == NULL)
return -1;
Window winRoot = XDefaultRootWindow(display);
Window winFocus;
int revert;
XGetInputFocus(display, &winFocus, &revert);

XKeyEvent event = createKeyEvent(display, winFocus, winRoot, 0, KEYCODE2);
event.state = XKeysymToKeycode(display, KEYCODE1);
XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);

XGetInputFocus(display, &winFocus, &revert);
event.keycode = XKeysymToKeycode(display, KEYCODE3);
event.state = XKeysymToKeycode(display, KEYCODE2);
XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);

event.type = KeyRelease;
XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);
event.state = XKeysymToKeycode(display, KEYCODE2);
XSendEvent(event.display, event.window, True, KeyPressMask, (XEvent *)&event);
XCloseDisplay(display);
return 0;
}

```

This was a task that I wanted to complete without grabbing xdotool and it was worth looking into learning all the ins and outs of the code, and I still don't understand some bits, but for the user that wants to start off and plugin and use based off of what is explained in other docs, this was my method to completing the task.

*actual purpose is it is to be used as a part of a program launcher from command line, and a new tab needed to be made in the current window, this will fork out the process to create the extra tab in the already opened window for the control-shift-t function*

P.S. this has also lead to the knowledge of the existence of the actual f13-f35 keys that are used as jokes online. I.e - Oh your having that problem, just press f15 : /

---

