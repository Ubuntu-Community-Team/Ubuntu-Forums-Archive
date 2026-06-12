---
title: "XLib - Setting Regions"
date: 2012-02-06
forum: Programming Talk
---

### Post by yank3s on 2012-02-06
Good afternoon community,

I've started to play with XLib a few days ago and I've got here a little problem. I am setting up a region, using the shape of a Polygon (A triangle in this case) as the Clipping area.
However, when I run my program, the computer's resources start to get consumed like crazy, the window doesn't move smoothly and the computer gets very very slow. I'll post the code here, perhaps someone will have an idea of what's going on .

```
/*
   Simple Xlib application drawing a box in a window.
   gcc input.c -o output -lX11
 */

#include <X11/Xlib.h>
#include <X11/X.h>
#include <X11/Xatom.h>
#include <X11/Xutil.h>
#include <X11/Xmd.h>
#include <X11/extensions/shape.h>
#include <X11/cursorfont.h>
#include "WindowsDataTypes.h"

#include "myshape.xbm"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <iostream>

#define BACKGROUND 0xFF0000 //RGB value for RED Color
#define YELLOW 0xFFFF00

using namespace std;

GC createGC (Display *d, Window w, string color) {
    GC newgc;
    XColor new_color;
    Colormap colormap = DefaultColormap(d, 0);;
    newgc = XCreateGC(d, w, 0, 0);
    XParseColor(d, colormap, color.c_str(), &new_color);
    XAllocColor(d, colormap, &new_color);
    XSetForeground(d, newgc, new_color.pixel);

    return newgc;
}

int main(void) {
    Display *d;
    Window w;
    XEvent e;
    char *msg = "Hello, World!";
    int s;

    /* open connection with the server */
    d = XOpenDisplay(NULL);
    if (d == NULL) {
        fprintf(stderr, "Cannot open display\n");
        exit(1);
    }

    s = DefaultScreen(d);


    /* create window */
    XSetWindowAttributes wattr;

#define MWM_HINTS_FUNCTIONS   0x00000001//(1L << 0)
#define MWM_HINTS_DECORATIONS 0x00000002//(1L << 1)
#define MWM_HINTS_INPUT_MODE  0x00000004//(1L << 2)
#define MWM_FUNC_MOVE           0x00000004//(1L << 2)
#define MWM_INPUT_MODELESS 0


    struct {
        long flags;
        long functions;
        long decorations;
        long inputmode;
    } prop;

    prop.flags=MWM_HINTS_FUNCTIONS|MWM_HINTS_DECORATIONS|MWM_HINTS_INPUT_MODE;
    prop.decorations=0;
    prop.functions=MWM_FUNC_MOVE;
    prop.inputmode=MWM_INPUT_MODELESS;

    XPoint points[3];
    points[0].x = 0;
    points[0].y = 0;
    points[1].x = 40;
    points[1].y = 0;
    points[2].x = 50;
    points[2].y = 50;
    //Region r = XPolygonRegion(points, 3, WindingRule);
    w = XCreateSimpleWindow(d, RootWindow(d, s), 300, 80, 300, 180, 0, YELLOW, BACKGROUND);
    w = XCreateWindow(d, RootWindow(d, s), 0, 0, 300, 180, 1, CopyFromParent, InputOutput, CopyFromParent, CopyFromParent , &wattr);
    GC gc =  createGC(d, w, "#00FF00");
    //XSetClipOrigin(d, gc, 0, 0);
    //XSetRegion(d,gc, r);
    printf("OLA\n");

    //Atom a=XInternAtom(d,"_MOTIF_WM_HINTS",0);
    //XChangeProperty( d, w, a, a, 32, PropModeReplace, (unsigned char*)&prop, 4);

    /* select kind of events we are interested in */
    XSelectInput(d, w, ExposureMask | KeyPressMask | ButtonPressMask);

    /* map (show) the window */
    XMapWindow(d, w);

    int xm = 0;
    int ym = 0;

    /* event loop */
    while (1) {
        XFillRectangle(d, w, gc, 20, 20, 50, 50);
    }

    /* close connection to server */
    XCloseDisplay(d);

    return 0;
}
```

In fact, I even commented the the Region zones just to check, and the same keeps happening. I've tried other projects on my computer that I took from internet, and they all work perfectly.

Thank you very much in advance

---

### Post by Arndt on 2012-02-06
> **yank3s said:**
> Good afternoon community,

I've started to play with XLib a few days ago and I've got here a little problem. I am setting up a region, using the shape of a Polygon (A triangle in this case) as the Clipping area.
However, when I run my program, the computer's resources start to get consumed like crazy, the window doesn't move smoothly and the computer gets very very slow. I'll post the code here, perhaps someone will have an idea of what's going on .

```
/*
   Simple Xlib application drawing a box in a window.
   gcc input.c -o output -lX11
 */

#include <X11/Xlib.h>
#include <X11/X.h>
#include <X11/Xatom.h>
#include <X11/Xutil.h>
#include <X11/Xmd.h>
#include <X11/extensions/shape.h>
#include <X11/cursorfont.h>
#include "WindowsDataTypes.h"

#include "myshape.xbm"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <iostream>

#define BACKGROUND 0xFF0000 //RGB value for RED Color
#define YELLOW 0xFFFF00

using namespace std;

GC createGC (Display *d, Window w, string color) {
    GC newgc;
    XColor new_color;
    Colormap colormap = DefaultColormap(d, 0);;
    newgc = XCreateGC(d, w, 0, 0);
    XParseColor(d, colormap, color.c_str(), &new_color);
    XAllocColor(d, colormap, &new_color);
    XSetForeground(d, newgc, new_color.pixel);

    return newgc;
}

int main(void) {
    Display *d;
    Window w;
    XEvent e;
    char *msg = "Hello, World!";
    int s;

    /* open connection with the server */
    d = XOpenDisplay(NULL);
    if (d == NULL) {
        fprintf(stderr, "Cannot open display\n");
        exit(1);
    }

    s = DefaultScreen(d);


    /* create window */
    XSetWindowAttributes wattr;

#define MWM_HINTS_FUNCTIONS   0x00000001//(1L << 0)
#define MWM_HINTS_DECORATIONS 0x00000002//(1L << 1)
#define MWM_HINTS_INPUT_MODE  0x00000004//(1L << 2)
#define MWM_FUNC_MOVE           0x00000004//(1L << 2)
#define MWM_INPUT_MODELESS 0


    struct {
        long flags;
        long functions;
        long decorations;
        long inputmode;
    } prop;

    prop.flags=MWM_HINTS_FUNCTIONS|MWM_HINTS_DECORATIONS|MWM_HINTS_INPUT_MODE;
    prop.decorations=0;
    prop.functions=MWM_FUNC_MOVE;
    prop.inputmode=MWM_INPUT_MODELESS;

    XPoint points[3];
    points[0].x = 0;
    points[0].y = 0;
    points[1].x = 40;
    points[1].y = 0;
    points[2].x = 50;
    points[2].y = 50;
    //Region r = XPolygonRegion(points, 3, WindingRule);
    w = XCreateSimpleWindow(d, RootWindow(d, s), 300, 80, 300, 180, 0, YELLOW, BACKGROUND);
    w = XCreateWindow(d, RootWindow(d, s), 0, 0, 300, 180, 1, CopyFromParent, InputOutput, CopyFromParent, CopyFromParent , &wattr);
    GC gc =  createGC(d, w, "#00FF00");
    //XSetClipOrigin(d, gc, 0, 0);
    //XSetRegion(d,gc, r);
    printf("OLA\n");

    //Atom a=XInternAtom(d,"_MOTIF_WM_HINTS",0);
    //XChangeProperty( d, w, a, a, 32, PropModeReplace, (unsigned char*)&prop, 4);

    /* select kind of events we are interested in */
    XSelectInput(d, w, ExposureMask | KeyPressMask | ButtonPressMask);

    /* map (show) the window */
    XMapWindow(d, w);

    int xm = 0;
    int ym = 0;

    /* event loop */
    while (1) {
        XFillRectangle(d, w, gc, 20, 20, 50, 50);
    }

    /* close connection to server */
    XCloseDisplay(d);

    return 0;
}
```

In fact, I even commented the the Region zones just to check, and the same keeps happening. I've tried other projects on my computer that I took from internet, and they all work perfectly.

Thank you very much in advance

Shouldn't your "event loop" actually wait for events?

---

### Post by yank3s on 2012-02-07
Thank you very much. I ended up forgetting that the "Expose" is also an event so basically the while loop was consuming a lot of resources. Thanks mate

---

