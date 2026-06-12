---
title: "Drawing a rotated rectangle with Xlib?"
date: 2008-10-28
forum: Programming Talk
---

### Post by tom66 on 2008-10-28
Would it be possible to draw a rotated rectangle using Xlib? If not, I can write my own function to do so, but what formula or equation would I need?

---

### Post by curvedinfinity on 2008-10-28
Heya, if you're going to get fancy-ish, its easiest to separate the actual rendering of the rectangle from the rotation (also called a transform step). Basically, in your drawRectangleRotated function, or whatever, first apply the rotation math to the individual corners of the rectangle. Then, after that's done, write a generic triangle-drawing function. With that generic drawTriangle, you can draw two of these triangles with the rotated rectangle corners and you will end up with a rotated rectangle. :)

If you need me to go over the different parts in more detail, just say so.

---

### Post by tom66 on 2008-10-28
The math part is the problem... how do I actually draw one? What is the maths behind it all?

---

### Post by stroyan on 2008-10-28
Rotation around the [0,0] origin is described by the sin and cosine
trig functions.  [http://mathworld.wolfram.com/RotationMatrix.html](http://mathworld.wolfram.com/RotationMatrix.html)
has a pretty good explaination of the rotation matrix.  To rotate
around another point you first shift the center of rotation to
the origin, rotate, then shift back.
You will need to include <math.h> and link with "-lm" to have
definitions of the sine and cosine functions.  Here is an example.
It increments a rotation angle for each keypress.
Hold down a repeating key to spin the rectangles.  Press "q"
to quit.  Note that the rotation of XPoint values won't work
well if you try to repeat it.  The integer precision of XPoint
will rapidly accumulate to big errors.  Keep your points in a
floating point format if you need to accumulate transformations.
```

#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/keysym.h>
#include <X11/keysymdef.h>
#include <locale.h>
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

void rotate(XPoint *points, int npoints, int rx, int ry, float angle)
{
    int i;
    for (i=0; i<npoints; i++) {
	float x, y;
	x = points[i].x - rx;
	y = points[i].y - ry;
	points[i].x =  rx + x * cosf(angle) - y * sinf(angle);
	points[i].y =  ry + x * sinf(angle) + y * cosf(angle);
    }
}

main()
{
    Display *d;
    Window w;
    XEvent e;
    GC gc;
    XGCValues gcv;
    KeySym keysym;
    XPoint points[5] = { { 10, 10 } , { 50, 10 } , { 50, 20 } , { 10, 20 } , { 10, 10 } };
    XPoint points2[4] = { { 60, 110 } , { 110, 110 } , { 110, 120 } , { 60, 120 } };
    XPoint rpoints[5];
    XPoint rpoints2[4];
    int i;
    int npoints = 5;
    int npoints2 = 4;
    float angle = 0.0;

    if(setlocale(LC_ALL, "") == NULL) {
	printf("cannot set locale\n");
	exit(1);
    }

    d = XOpenDisplay(NULL);
    w = XCreateSimpleWindow(d, RootWindow(d,0), 400,300,500,400,2,0,1);
    gc = XCreateGC(d, w, 0, &gcv);
    XSetForeground(d, gc, WhitePixel(d, 0));
    XSetBackground(d, gc, BlackPixel(d, 0));

    XSelectInput(d, w, ExposureMask | KeyPressMask);
    XMapWindow(d, w);

    while (1) {
	XNextEvent(d, &e);

	switch(e.type) {
	case KeyPress:
	    angle += 0.1;
	    if (XKeycodeToKeysym(d, e.xkey.keycode, 0) == XStringToKeysym("q")) exit(0);
	    /* fall through to expose */

	case Expose:
	    for (i=0;i<npoints;i++) rpoints[i] = points[i];
	    for (i=0;i<npoints2;i++) rpoints2[i] = points2[i];
	    rotate(rpoints, npoints, 30, 15, angle);
	    rotate(rpoints2, npoints2, 85, 115, angle);
	    XClearWindow(d, w);
	    XDrawLines(d, w, gc, rpoints, npoints, CoordModeOrigin);
	    XFillPolygon(d, w, gc, rpoints2, npoints2, Convex, CoordModeOrigin);
	    XFlush(d);
	    break;
	}
    }
}

```

---

### Post by tom66 on 2008-10-28
Thanks, much appreciated!

---

