---
title: "Xwindows - window without a DE frame?"
date: 2008-01-13
forum: Programming Talk
---

### Post by KPexEA on 2008-01-13
After opening a window with XCreateSimpleWindow, is there a way to hide the Window frame that is automatically added by the window enviroment, so my code can draw to the whole window?

Thanks,
Kevin

---

### Post by wolfbone on 2008-01-13
Do you mean the window decorations?

When the override_redirect attribute is set on the window with XCreateWindow() -  presumably you'd have to use XChangeWMAttributes() if you're using XCreateSimpleWindow() - I've noticed I get no WM decorations, but that's not a good way to do it for a normal window. 

There is potentially (I found it in a ML) a better way, in lieu of any help from the EWMH spec, which I haven't actually tried, which goes something like this:

[PHP]	typedef struct {
	    CARD32 flags;
	    CARD32 functions;
	    CARD32 decorations;
	    INT32 input_mode;
	    CARD32 status;
	} MotifWmHints, MwmHints;

	#define MWM_HINTS_DECORATIONS   (1L << 1)

	...

	Atom XA_MOTIF_WM_HINTS = XInternAtom(maindpy, "_MOTIF_WM_HINTS", False);
	MotifWmHints mwm_hints;

	mwm_hints.flags = MWM_HINTS_DECORATIONS;
	mwm_hints.decorations = 0;

	XChangeProperty(
		maindpy, mainwin,
		XA_MOTIF_WM_HINTS, XA_MOTIF_WM_HINTS,
		32, PropModeReplace,
		(char *) &mwm_hints, 5
	);
[/PHP]

For a full-screen window - if that's what you want -  there is a different way involving setting the  _NET_WM_STATE_FULLSCREEN property.

---

### Post by KPexEA on 2008-01-13
Thanks VERY much, that is exactly what  was looking for,
Cheers,
Kevin

---

