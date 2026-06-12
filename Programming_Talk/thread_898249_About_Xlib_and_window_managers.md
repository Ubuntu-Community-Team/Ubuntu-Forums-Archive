---
title: "About Xlib and window managers"
date: 2008-08-23
forum: Programming Talk
---

### Post by techmarks on 2008-08-23
If I create a small test app using only Xlib (to create a window on the screen) and Cairo (to draw stuff on the window) and then run it in my desktop (Xfce in this case) it works fine.

Now if I just try to run it from the command line I get a message about something like 'failure to initialize display' I (think that's what it was)

So I'm wondering how do the desktop and window managers work?

Suppose I use Xlib to just create a big window and then want to run it (but without starting Xfce first) could I even do it?
There must be a way, because that must be basically what Xfce is doing somehow and ultimately it's the X Window system behind it.

If someone could share some insight into how the process works I'd appreciate it. thanks.


(even if I just try to start up the plain simple window by itself without using Cairo at all even, it can't just be started from a command line)

---

### Post by crdlb on 2008-08-24
What exactly is your goal in this?

X uses a client-server model, where the X server (AKA Display) draws graphics on the screen and each client application can open a connection to that server for creating windows, etc. If you attempt to run an X application from the command line, it will fail to run since there is no server running to which it can connect. In the Xlib API, `XOpenDisplay (NULL)` will check the environment variable DISPLAY to find the string representing the current Display. You can set that variable to ":0.0" to connect to an X server running at ":0" (the ".0" represents the Screen number and is optional).

Excluding some sort of embedded or kiosk-like setup, you should always allow your display manager to start the X server for you (gdm is the one used by default on ubuntu and xubuntu). The window manager (or full desktop environment) started by the display manager is configurable, so you could even make it start your Xlib app directly, although it probably wouldn't be too useful to do that.

---

