---
title: "intro to window manager programming?"
date: 2008-10-13
forum: Programming Talk
---

### Post by hessiess on 2008-10-13
I've been thinking about writing a 'blender-like' tiling window manager for a few months. i have a resalable understanding of C++, however I don't know how X window managers, or the xlib/XCB API's work. so as of yet, ive been unable to understand the source code of the WM's ive looked at (DWM). are there any 'intro to WM programming' tutorials.

thanks.

---

### Post by hessiess on 2008-10-13
bump?

---

### Post by LaRoza on 2008-10-13
[http://freshmeat.net/projects/tinywm/](http://freshmeat.net/projects/tinywm/)

TinyWM is the smallest in code that I know of, it would be a good start.

---

### Post by hessiess on 2008-10-13
thanks laroza, il take a look at that and see if it makes sense :)

---

### Post by hessiess on 2008-10-14
So, ive hit anouther brick wall. Im trying to experement with the tinywm source code, but I cannot run the window manager, as Awesome is already running. is it possable to create a window within the current window manager, that is running a differnt window manager, amd can have apps opened within it?

shutting down one WM, and starting anotuher one is anoying, espetily if I made a bug, and it crasshes, leaving me with no WM, and thus have to restart X.

---

### Post by doorman on 2008-10-14
you could set up a testing virtual machine and restart X there every time

---

### Post by stroyan on 2008-10-14
You can use the Xnest command from the xnest package to run an X server
as a client to another X server.  You probably want to unset XAUTHORITY
so your clients don't need an xauth entry for the new X server.  Or you
could use xauth to set a cookie for the other X server.
```

 unset XAUTHORITY; Xnest :3 & sleep 2; DISPLAY=:3 xterm

```

There is also a mechanism to run Xorg on multiple virtual terminals
using the vt*XX* option to select which virtual terminal to use.
Then the different X servers can be selected with <ctrl><alt>,F*N*>.
But that doesn't seem as nice as simultaneously seeing both the xnest
window and a debugger in the original X server.

---

### Post by hessiess on 2008-10-14
> **stroyan said:**
> You can use the Xnest command from the xnest package to run an X server
as a client to another X server.  You probably want to unset XAUTHORITY
so your clients don't need an xauth entry for the new X server.  Or you
could use xauth to set a cookie for the other X server.
```

 unset XAUTHORITY; Xnest :3 & sleep 2; DISPLAY=:3 xterm

```

There is also a mechanism to run Xorg on multiple virtual terminals
using the vt*XX* option to select which virtual terminal to use.
Then the different X servers can be selected with <ctrl><alt>,F*N*>.
But that doesn't seem as nice as simultaneously seeing both the xnest
window and a debugger in the original X server.

Thanks, il try that :)

Ive got some problem with Xlib events, what im trying to do is  edit tinywm to alow you to move windows around with 'h,j,k,l':

[PHP]/*create key binding*/
		KeyCode KEY_H;
		KEY_H = XKeysymToKeycode(dpy, XStringToKeysym("H")); 

	    XGrabKey(dpy, KEY_H, Mod1Mask, root,
		    True, GrabModeAsync, GrabModeAsync);

	    for(;;)
	    {
	/* loop through events*/
		XNextEvent(dpy, &ev);

	/* move window with H key*/	
		if(ev.type == KeyPress)
		{
			if(ev.xkey.subwindow == KEY_H)
			{
				XGetWindowAttributes(dpy, ev.xbutton.subwindow, &attr);
				XMoveWindow(dpy, ev.xmotion.window, attr.x + 20, attr.height);
				printf("aaa");
			}

		}[/PHP]
what that should do is move a window if the 'h' key is pressed, but nothing happens.

---

### Post by stroyan on 2008-10-14
Your XGrabKey call is passing Mod1Mask which would require <alt>h.
Perhaps you want AnyModifier there.

You are comparing ev.xkey.subwindow instead of ev.xkey.keycode.

You are using ev.xbutton.subwindow and ev.xmotion.window for a
key event.  You should only use the union member name that matches
the type of the event.

---

