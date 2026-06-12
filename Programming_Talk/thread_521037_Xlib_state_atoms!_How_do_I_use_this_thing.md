---
title: "Xlib state atoms! How do I use this thing?"
date: 2007-08-08
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2007-08-08
I made the foolish decision to start messing with gnome-panel. What I want is an option to have panels appear behind normal windows and not set struts, thus achieving tidy desklets (very much like those of Windows Vista) under a single infrastructure. With that and some fancy applets that take advantage of the idea, it should be quite possible to have Gnome working very nicely with the informative / pretty looking desklets idea.

Unfortunately for me, this has come to involve immense pain since I have never used (or learned) xlib, and it turns out to be a horrendously complicated library to just learn on the spot.
I promise, I'll learn XLib soon!
For now, maybe someone can help me out?

I have read up on [extended window manager hints](http://standards.freedesktop.org/wm-spec/wm-spec-1.3.html), which tells me that what I want is indeed possible.
I can add the _NET_WM_STATE_BELOW atom to _NET_WM_STATE, which will (should) override the default behaviour of dock windows to be always above everything else, instead making them always below normal windows, above the desktop in stacking order.

Here is a chunk of the source code from gnome-panel's panel-xutils.c:
```
/*
 * panel-xutils.c: X related utility methods.
 *
 * Copyright (C) 2003 Sun Microsystems, Inc.
 *
 * This program is free software; you can redistribute it and/or
 * modify it under the terms of the GNU General Public License as
 * published by the Free Software Foundation; either version 2 of the
 * License, or (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA
 * 02111-1307, USA.
 *
 * Authors:
 *	Mark McLoughlin <mark@skynet.ie>
 */

#include "config.h"

#include "panel-xutils.h"

#include <glib.h>
#include <gdk/gdk.h>
#include <gdk/gdkx.h>
#include <X11/Xlib.h>
#include <X11/Xatom.h>

static Atom net_wm_window_type        = None;
static Atom net_wm_window_type_dock   = None;
static Atom net_wm_window_type_normal = None;
static Atom net_wm_strut              = None;
static Atom net_wm_strut_partial      = None;

void
panel_xutils_set_window_type (GdkWindow             *gdk_window,	
			      PanelXUtilsWindowType  type)
{
	Display *display;
	Window   window;
	Atom     atoms [2];
	int      i = 0;

	g_return_if_fail (GDK_IS_WINDOW (gdk_window));

	display = GDK_WINDOW_XDISPLAY (gdk_window);
	window  = GDK_WINDOW_XWINDOW (gdk_window);

	if (net_wm_window_type == None)
		net_wm_window_type = XInternAtom (display,
						  "_NET_WM_WINDOW_TYPE",
						  False);

	switch (type) {
	case PANEL_XUTILS_TYPE_DOCK:
		if (net_wm_window_type_dock == None)
			net_wm_window_type_dock = XInternAtom (display,
							       "_NET_WM_WINDOW_TYPE_DOCK",
							       False);
		atoms [i++] = net_wm_window_type_dock;
		break;
	case PANEL_XUTILS_TYPE_NORMAL:
		if (net_wm_window_type_normal == None)
			net_wm_window_type_normal = XInternAtom (display,
								 "_NET_WM_WINDOW_TYPE_NORMAL",
								 False);
		atoms [i++] = net_wm_window_type_normal;
		break;
	default:
		g_assert_not_reached ();
		break;
	}
	
	//TODO: Must set state atom: "_NET_WM_STATE_BELOW"

	gdk_error_trap_push ();
	XChangeProperty (display, window, net_wm_window_type,
			 XA_ATOM, 32, PropModeReplace,
			 (guchar *) &atoms, i);
	gdk_error_trap_pop ();
}
```

In this case, type is PANEL_XUTILS_TYPE_DOCK.
As far as setting this atom is concerned, I am baffled :(

I have tried adding the following code at the end of that function:
```
Atom state_below;
state_below = XInternAtom (display, "_NET_WM_STATE_BELOW", False);

XChangeProperty (display, window,
	XInternAtom (display,"_NET_WM_STATE",False),
	XA_ATOM, 32, PropModeReplace,
	(guchar *) &state_below, 1);
```
I have also tried putting that code in its own function called slightly later on, (called from panel_toplevel_realize).
However, it isn't giving me any change.

A bit of searching told me to use xprop, and the panel window's _NET_WM_STATE atom is unchanged:
```

XProp output:
_NET_WM_STATE(ATOM) = _NET_WM_STATE_SKIP_PAGER, _NET_WM_STATE_SKIP_TASKBAR
```

I'm a bit lost, but I would really love to have this ball rolling (and I promise I will not try to write the applets with C). Are there any xlib people among us who can help?

---

### Post by moma on 2007-08-09
Hello, 

Not sure if this is right, but study the attached code sample. "xtest1.c"
Look for the lines below "[COLOR="Purple"]// Window at the background test[/COLOR]".

Compile it 
$ gcc -lX11 -lXext xtest1.c -o xtest1

Run it 
$ ./xtest1

Agree: XLib is is a bit tricky some times ...

EDIT: Error in the code. Fixed it.

---

### Post by Mr. Picklesworth on 2007-08-09
Thank you, that example is pretty helpful. Rather encouraging, actually!

Gnome-panel uses an insane combination of xlib and gdk commands. I cannot comprehend the reason behind this, since gdk is a gentle wrapper for that stuff anyway!
I'm sure there is a reason for it all, however, which I will discover as I learn more about xlib...

I figured out my problem was that I was trying to change the state after the window was mapped. Doing that involves some bloody scary message handling stuff and doesn't need to be done in this case anyway, so I should have instead tried that before the window was mapped. Then I noticed that panel_toplevel_realize already uses quite a few gtk functions, so I found gtk_window_set_keep_below and called that in there and it works. Nice and easy, if I discount the numerous hours it took to come to that one-line solution :)
(Next up: gconf!).

---

### Post by Mr. Picklesworth on 2007-08-11
Yay, a new question!

Now I have moved on to struts with this project, and it's looking pretty hopeful. However, the way that the panels interact with each-other seems very heavily influenced by their struts such that pulling them out causes really weird and horrible things. Is there a magical way to filter the windows that are affected by struts, perhaps by their window types? (Or something like struts that will do this, since struts don't sound like they should be doing it).
What I want to have is other Dock windows and the Desktop influenced by struts in the way they seem to be, but Normal windows to not be affected by them.
I am of course hoping for a single miraculous command, but any insight would be jolly.

---

### Post by theOGRE on 2010-08-01
Thanks for the sample code moma. It was what I needed to get me started.

---

