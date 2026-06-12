---
title: "X11- No MotionNotify Event when mouse down"
date: 2011-09-30
forum: Programming Talk
---

### Post by firefly431 on 2011-09-30
First of all, my mouse is working.
Here is my code: (I have a GC called GC, a display called dpy, and a Window called w)
```

    int x=-1;
    int y=-1;
    int dx, dy;
    for (;;) {
        XEvent e;
        XNextEvent(dpy, &e);
        switch (e.type) {
            case Expose:
                printf("Expose Event!\n");
                fflush(stdout);
                if (e.xexpose.count > 0)
                    break;
                //XDrawLine(dpy, w, gc, 10, 60, 180, 20);
                break;
            case MotionNotify:
                dx = e.xmotion.x;
                dy = e.xmotion.y;
                printf("State: %x\n",e.xmotion.state);
                if (e.xmotion.state & Button1Mask) {
                    if (x == -1) {
                        x=dx;
                        y=dy;
                    }
                    XDrawLine(dpy,w,gc,x,y,dx,dy);
                    printf("Drag!\n");
                    fflush(stdout);
                } else {
                    x=-1;
                    y=-1;
                }
                break;
            default:
                break;
        }
    }

```It prints a whole bunch of State: 0's but when I click, it stops.

---

### Post by scitron on 2011-09-30
Have you set the event mask of your window properly?

See [here. ]("http://tronche.com/gui/x/xlib/events/keyboard-pointer/keyboard-pointer.html")

For what you are attempting to do here you might also consider using the XQueryPointer function.

---

### Post by firefly431 on 2011-10-01
XSelectInput(dpy, w, ExposureMask | PointerMotionMask | ButtonMotionMask | Button1MotionMask);

---

### Post by scitron on 2011-10-02
Your XSelectInput() call looks good to me but there are a few things I don't get about your event loop.

Why is the following declared in the event loop?

```


XEvent e;

```

While this isn't the problem, it's just not needed there just declare e before the event loop once.

It seems your are using XDrawLine() to draw points why don't you just use XDrawPoint() ??

What exactly is this supposed to do?

Are you trying to draw lines  when the user moves the mouse, or when the
user clicks a button, or both?

What are you trying to do with the "state" member of the MotionNotify event?

I wrote a small program to draw points when the mouse (pointer) is moved around in a window and I used the MotionNotify event, it works.

Perhaps the problem is with the way you set up your GC.

---

### Post by firefly431 on 2011-10-02
I'm not drawing points, It's like in a drawing program how they don't draw points. They connect them with a line. X is getting really annoying so I'm going to try Qt.

---

### Post by gmargo on 2011-10-02
I wrote a little test program using the **xev** source code, and was able to duplicate your results.

I found that adding these to your event mask will enable the motion notify events you're looking for:
```

ButtonPressMask | ButtonReleaseMask

```

---

### Post by scitron on 2011-10-02
> **firefly431 said:**
> I'm not drawing points, It's like in a drawing program how they don't draw points. They connect them with a line. X is getting really annoying so I'm going to try Qt.


I think I understand what you want to accomplish now.

It certainly can be done with just Xlib.

For just drawing to a window with mouse and keyboard controls or even drawing to an OpenGL window with GLX it's good.

Eventually you might want to interact with the user and you'll need input boxes and edit controls etc. at that point programming GUI controls with just Xlib will be lots of work and for what? they've already been implemented by the GUI toolkits.

---

