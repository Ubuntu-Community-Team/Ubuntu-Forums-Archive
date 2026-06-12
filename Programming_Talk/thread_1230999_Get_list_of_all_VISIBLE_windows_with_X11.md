---
title: "Get list of all VISIBLE windows with X11"
date: 2009-08-04
forum: Programming Talk
---

### Post by JustAnotherVagueAnon on 2009-08-04
Hi, I'm writing a program in C using X11/Xlib and have been using XQueryTree to get a list of all the windows. This returns over 100 windows when there should be only a few visible. Using the known position of the window and printing XWindowAttributes for each window obtained with XQueryTree I have found the windows which are the ones I want to find, but I can find no way to distinguish between these and the non visible windows. I tried checking whether these had different XWindowAttributes than the non visible windows, but there is nothing definitive. Does anyone know a way to get only the VISIBLE windows?

Note: I'd prefer to do this entirely with Xlib, but if anyone knows how to do it using an external program, that would also work. Thanks!

---

### Post by BurntSushi on 2009-08-19
If you're okay with using EWM Hints, then check the "_NET_CLIENT_LIST" property on the root window. This will ask the current window manager what clients are currently visible. (This returns a list of window ids- you'll need to create a window resource with this.)

This may also return dock applications or panels. So you should check that it's on a valid desktop, and also check that the "_NET_WM_STATE_SKIP_TASKBAR" atom is set in the "_NET_WM_STATE" property (on the given window).

Additionally, if you want to ignore "pop up windows" check into the "_NET_WM_STATE_MODAL" atom in the "_NET_WM_STATE" property and possible its transient.

See [http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/) and [http://standards.freedesktop.org/wm-spec/wm-spec-1.3.html](http://standards.freedesktop.org/wm-spec/wm-spec-1.3.html) for more information.

Hope that helps a little bit.

---

