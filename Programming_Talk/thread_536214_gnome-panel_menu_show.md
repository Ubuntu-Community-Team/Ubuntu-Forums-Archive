---
title: "gnome-panel menu show"
date: 2007-08-27
forum: Programming Talk
---

### Post by u-foka on 2007-08-27
Hy there!

I'm using xfwm4 as window manager with gnome, because it's stable & fast compositor. Some days ago I decided to find a solution to show the gnome menu with hot-key from xfwm, but I can't. :S So today I got the metacity-s source package and looked into it, to find out how metacity calls the gnome-panel to show the menu.

The code i wrote looks like this:
```
Display			*xdisplay;
XClientMessageEvent	xevent;

xdisplay = XOpenDisplay(NULL);

char *atom_names[] = {
    	"_GNOME_PANEL_ACTION",
    	"_GNOME_PANEL_ACTION_MAIN_MENU",
    	"_GNOME_PANEL_ACTION_RUN_DIALOG"
};
Atom atoms[G_N_ELEMENTS(atom_names)];

XInternAtoms (xdisplay, atom_names, G_N_ELEMENTS (atom_names), False, atoms);

xevent.type			= ClientMessage;
xevent.window		= DefaultRootWindow(xdisplay);
xevent.message_type	= atoms[0];
xevent.format		= 32;
xevent.data.l[0]	= atoms[1];
xevent.data.l[1]	= CurrentTime;

XUngrabKeyboard (xdisplay, CurrentTime);

XSendEvent (xdisplay,
      DefaultRootWindow(xdisplay),
      False,
      StructureNotifyMask,
      (XEvent*) &xevent);
```
It's seem to work, but does nothing... :S

So my questions is:
Why it isn't work???? :D
How can I show debug information from gnome-panel and metacity (What is not running when i test my application, but I want to see it's debug information when it's calling the gnome-panel :P)

Thx :)

---

