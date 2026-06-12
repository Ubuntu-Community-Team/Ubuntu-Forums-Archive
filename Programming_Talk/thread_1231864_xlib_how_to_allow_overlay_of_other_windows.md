---
title: "xlib: how to allow overlay of other windows?"
date: 2009-08-05
forum: Programming Talk
---

### Post by parvata on 2009-08-05
Hi,

I am using the feh slideshow program in full-screen mode. While the slide show is in progress I would like to draw some other windows (something like clock or calendar from gdesklets) on top of this slideshow. Currently feh does not allow me to do that. Below is the code that feh uses to create a window. Any ideas on how to allow feh to give focus to other windows while it is playing the slide show? I have posted a question to feh but looks like the project is dead. Any ideas or information is really appreciated.

XSetWindowAttributes attr;
XClassHint *xch;
MWMHints mwmhints;
Atom prop = None;
attr.backing_store = NotUseful;
attr.override_redirect = False;
attr.colormap = cm;
attr.border_pixel = 0;
attr.background_pixel = 0;
attr.save_under = False;
attr.event_mask =
StructureNotifyMask | ButtonPressMask | ButtonReleaseMask |
PointerMotionMask | EnterWindowMask | LeaveWindowMask | KeyPressMask |
KeyReleaseMask | ButtonMotionMask | ExposureMask | FocusChangeMask |
PropertyChangeMask | VisibilityChangeMask;

if (opt.borderless || ret->full_screen) {
prop = XInternAtom(disp, "_MOTIF_WM_HINTS", True);
if (prop == None) {
weprintf("Window Manager does not support MWM hints. "
"To get a borderless window I have to bypass your wm.");
attr.override_redirect = True;
mwmhints.flags = 0;
} else {
mwmhints.flags = MWM_HINTS_DECORATIONS;
mwmhints.decorations = 0;
}
} else
mwmhints.flags = 0;

ret->win =
XCreateWindow(disp, DefaultRootWindow(disp), x, y, w, h, 0, depth,
InputOutput, vis,
CWOverrideRedirect | CWSaveUnder | CWBackingStore |
CWColormap | CWBackPixel | CWBorderPixel | CWEventMask,
&attr);

if (mwmhints.flags) {
XChangeProperty(disp, ret->win, prop, prop, 32, PropModeReplace,
(unsigned char *) &mwmhints, PROP_MWM_HINTS_ELEMENTS);
}

XSetWMProtocols(disp, ret->win, &wmDeleteWindow, 1);

---

