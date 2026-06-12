---
title: "C++: Drawing on the root screen"
date: 2009-08-24
forum: Programming Talk
---

### Post by WitchCraft on 2009-08-24
Question: I'm using the code below.

I want to draw a rectangle (or a line or a point alternatively) directly on the root screen.

I use the program below (also moves the mouse pointer)
The mouse works fine, but it doesn't draw a rectangle... why ?
Ultimately, I want to get/set individual pixels, and write text and/or shapes to the root window.

I've already managed to do so on windows, but on Linux I don't seem to be able to draw on the root/Desktop screen...

```

#include <iostream>
#include <cstdlib>
#include <X11/Xlib.h>
// Compile: g++ mypointer.c -o my -lX11

// cc prog.c -o prog -L/usr/X11/lib -lX11
// or perhaps this (for a system with release 6 of X11):

//cc prog.c -o prog -L/usr/X11R6/lib -lX11

// On SunOs 4 systems, the X libraries are placed in /usr/openwin/lib:
// cc prog.c -o prog -L/usr/openwin/lib -lX11



/*
Ecore and Evas (XLib abstraction and canvas library) will allow you to
construct windows, place objects, buttons if needed, get / use scroll
/ warp events etc. very easily.  In Ecore/Evas, you can register
events with callbacks and do certain actions based on that. This makes
things like clicking / scrolling very simple. You could also track the
mouse movement / warp it easily. Ecore provides and event loop so you
just have to hook your application into the loop and register the
appropriate callbacks. If you feel you require a solid example or a
small tutorial then this could be the topic of our next (soon to be
held) meeting.
*/

void move_mouse_pointer(int delta_x, int delta_y)
{
// Opening and closing the display each time is not the right way to do this.
    Display *display = XOpenDisplay(0);
    XWarpPointer(display, None, None, 0, 0, 0, 0, delta_x, delta_y);
// XWarpPointer (dpy, scr->Root, scr->Root, 0, 0, scr->MyDisplayWidth, scr->MyDisplayHeight, x, y);

    XCloseDisplay(display);
}

/*
XWarpPointer(display, src_w, dest_w, src_x, src_y, src_width, src_height, dest_x,
                dest_y)
        Display *display;
        Window src_w, dest_w;
        int src_x, src_y;
        unsigned int src_width, src_height;
        int dest_x, dest_y;

Arguments

display	 Specifies the connection to the X server.
src_w	 Specifies the source window or None.
dest_w	 Specifies the destination window or None.
src_x
src_y
src_width
src_height	 Specify a rectangle in the source window.
dest_x
dest_y
*/





int GetMousePosition()
{
  Display *d;
  Window inwin;      /* root window the pointer is in */
  Window inchildwin; /* child win the pointer is in */
  int rootx, rooty; /* relative to the "root" window; we are not interested in these,
                       but we can't pass NULL */
  int childx, childy;  /* the values we are interested in */
  Atom atom_type_prop; /* not interested */
  int actual_format;   /* should be 32 after the call */
  unsigned int mask;   /* status of the buttons */
  unsigned long n_items, bytes_after_ret;
  Window *props; /* since we are interested just in the first value, which is
		    a Window id */

  /* default DISPLAY */
  d = XOpenDisplay(NULL);

  /* ask for active window (no error check); the client must be freedesktop
     compliant */
  (void)XGetWindowProperty(d, DefaultRootWindow(d),
			   XInternAtom(d, "_NET_ACTIVE_WINDOW", True),
			   0, 1, False, AnyPropertyType,
			   &atom_type_prop, &actual_format,
			   &n_items, &bytes_after_ret, (unsigned char**)&props);

  XQueryPointer(d, props[0], &inwin,  &inchildwin,
		&rootx, &rooty, &childx, &childy, &mask);
  printf("relative to active window: %d,%d\n", childx, childy);

  XFree(props);           /* free mem */
  (void)XCloseDisplay(d); /* and close the display */
  return 0;
}

int GetGlobalMousePosition()
{Display *dsp = XOpenDisplay( NULL );
if( !dsp ){ return 1; }

int screenNumber = DefaultScreen(dsp);

XEvent event;

/* get info about current pointer position */
XQueryPointer(dsp, RootWindow(dsp, DefaultScreen(dsp)),
&event.xbutton.root, &event.xbutton.window,
&event.xbutton.x_root, &event.xbutton.y_root,
&event.xbutton.x, &event.xbutton.y,
&event.xbutton.state);

printf("Mouse Coordinates: %d %d\n", event.xbutton.x, event.xbutton.y);

XCloseDisplay( dsp );
}

int main()
{
    /* this variable will contain the pointer to the Display structure */
    /* returned when opening a connection.                             */

    GetGlobalMousePosition();
    GetMousePosition();

    Display* display;

    /* open the connection to the display "simey:0". */
    display = XOpenDisplay(0);// display = XOpenDisplay("simey:0");
    if (display == NULL)
    {
        fprintf(stderr, "Cannot connect to X server %s\n", "simey:0");
        exit (-1);
    }

    char green[] = "#00FF00";
    GC green_gc;
    Colormap colormap;
    XColor green_col;


    colormap = DefaultColormap(display, 0);

    XGrabServer(display);
    green_gc = XCreateGC(display,RootWindow(display, DefaultScreen(display)), 0, 0);
    XParseColor(display, colormap, green, &green_col);
	XAllocColor(display, colormap, &green_col);
	XSetForeground(display, green_gc, green_col.pixel);


    XDrawRectangle(display,RootWindow(display, DefaultScreen(display)), green_gc, 10, 10, 497, 497);
    //XFlush(display);

    XUngrabServer(display);

    int screen_height = DisplayHeight(display, DefaultScreen(display));
    int screen_width  = DisplayWidth(display, DefaultScreen(display));
    printf("This screen is (%d,%d)\n", screen_width, screen_height);

    XCloseDisplay( display );

    int delta_x =30;
    int delta_y =50;
    move_mouse_pointer(delta_x,delta_y);
    return 0;
}

```

---

### Post by WitchCraft on 2009-08-25
bump

---

### Post by moma on 2009-08-25
Hello,

Test this piece of code.
Copy & paste it before your XUngrabServer(display) line.

```
int screen_num = DefaultScreen(display);
Screen *screen = XScreenOfDisplay(display, screen_num);
Window root_win = RootWindow(display, XScreenNumberOfScreen(screen));

/* Create a GC (Graphics Context) for the line  */
XGCValues gc_val;
gc_val.function           = GXxor;
gc_val.plane_mask         = AllPlanes;
gc_val.foreground         = WhitePixel(display, screen_num);
gc_val.background         = BlackPixel(display, screen_num);
gc_val.line_width         = 4;
gc_val.line_style         = LineSolid;
gc_val.cap_style          = CapButt;
gc_val.join_style         = JoinMiter;
gc_val.fill_style         = FillOpaqueStippled;
gc_val.fill_rule          = WindingRule;
gc_val.graphics_exposures = False;
gc_val.clip_x_origin      = 0;
gc_val.clip_y_origin      = 0;
gc_val.clip_mask          = None;
gc_val.subwindow_mode     = IncludeInferiors;

GC  gc_line = XCreateGC(display, root_win, GCFunction | GCPlaneMask |  GCForeground | GCBackground | GCLineWidth | GCLineStyle |
	        GCCapStyle  | GCJoinStyle  |  GCFillStyle  |  GCFillRule  |  GCGraphicsExposures |
	        GCClipXOrigin |  GCClipYOrigin  |  GCClipMask  | GCSubwindowMode, &gc_val);

/* XSetForeground(display, gc_line, some_color); */
XDrawRectangle(display, root_win, gc_line, 50, 50, 400, 400);

```

At least it draws a rectangle on the root_win, but it will disappear if other windows overlap or refresh that spot (keep your terminal window away). Notice also that the sample uses GXxor function to draw the line.
 
I copied it from my [Gscreendump...]("http://code.google.com/p/gscreendump/") product (file: src/sd_capture_area.c)
You are welcome to download it, take a [look at it...]("http://code.google.com/p/gscreendump/source/browse/#svn/trunk/src") or contribute.
----

[COLOR="Red"]ps.[/COLOR] Do not forget to check this super-fresh Android guide:
[http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html](http://www.futuredesktop.org/developing_android_apps_on_ubuntu.html)

---

### Post by WitchCraft on 2009-08-25
> **moma said:**
> Hello,

Test this piece of code.
Copy & paste it before your XUngrabServer(display) line.
tu.html

At least it draws a rectangle on the root_win, but it will disappear if other windows overlap or refresh that spot (keep your terminal window away). Notice also that the sample uses GXxor function to draw the line.

Thanks, works perfectly.

The disappearance is like in windows, and like in Windows, it can probably be solved by getting the screen update /paint / change event in case the redraw event is issued.

```

#include <iostream>
#include <cstdlib>
#include <X11/Xlib.h>
// Compile: g++ mypointer.c -o my -lX11

// cc prog.c -o prog -L/usr/X11/lib -lX11
// or perhaps this (for a system with release 6 of X11):

//cc prog.c -o prog -L/usr/X11R6/lib -lX11

// On SunOs 4 systems, the X libraries are placed in /usr/openwin/lib:
// cc prog.c -o prog -L/usr/openwin/lib -lX11

int main()
{
    /* this variable will contain the pointer to the Display structure */
    /* returned when opening a connection.                             */


    Display* display;

    /* open the connection to the display "simey:0". */
    display = XOpenDisplay(0);// display = XOpenDisplay("simey:0");
    if (display == NULL)
    {
        fprintf(stderr, "Cannot connect to X server %s\n", "simey:0");
        exit (-1);
    }

  XGrabServer(display);

int screen_num = DefaultScreen(display);
Screen *screen = XScreenOfDisplay(display, screen_num);
Window root_win = RootWindow(display, XScreenNumberOfScreen(screen));

/* Create a GC (Graphics Context) for the line  */
XGCValues gc_val;
gc_val.function           = GXxor;
gc_val.plane_mask         = AllPlanes;
gc_val.foreground         = WhitePixel(display, screen_num);
gc_val.background         = BlackPixel(display, screen_num);
gc_val.line_width         = 4;
gc_val.line_style         = LineSolid;
gc_val.cap_style          = CapButt;
gc_val.join_style         = JoinMiter;
gc_val.fill_style         = FillOpaqueStippled;
gc_val.fill_rule          = WindingRule;
gc_val.graphics_exposures = False;
gc_val.clip_x_origin      = 0;
gc_val.clip_y_origin      = 0;
gc_val.clip_mask          = None;
gc_val.subwindow_mode     = IncludeInferiors;

GC  gc_line = XCreateGC(display, root_win, GCFunction | GCPlaneMask |  GCForeground | GCBackground | GCLineWidth | GCLineStyle |
	        GCCapStyle  | GCJoinStyle  |  GCFillStyle  |  GCFillRule  |  GCGraphicsExposures |
	        GCClipXOrigin |  GCClipYOrigin  |  GCClipMask  | GCSubwindowMode, &gc_val);

/* XSetForeground(display, gc_line, some_color); */
XDrawRectangle(display, root_win, gc_line, 50, 50, 400, 400);

 XFlush(display);
  XUngrabServer(display);


   XCloseDisplay( display );

}


```

---

### Post by moma on 2009-08-25
> **WitchCraft said:**
> The disappearance is like in windows, and like in Windows, it can probably be solved by getting the screen update /paint / change event in case the redraw event is issued.Yes in deed.
--
In Gscreendump I use it to draw a selection rectangle on the screen and then grab a screenshot of that area. The rectangle (lines) disappear when you draw it twice with Xor function. 
gc_val.function = GXxor.

Take also look at GNOME's [GDK...]("http://library.gnome.org/devel/gdk/stable/") and [GTK...]("http://library.gnome.org/devel/gtk/stable/") libraries. Xlib is rather low level. Gscreendump uses them all.

---

### Post by Marco A on 2009-08-25
.

---

### Post by WitchCraft on 2009-08-25
> **Marco A said:**
> Both of the previous examples were very helpful, thanks.

I've modified your original programs' drawing routine so that it works also.

This version is using the OPs' gc.  The gc is set up the same way to create a green rectangle.

I also made a few minor unrelated changes in opening the display.

The XGrabServer() and XUngrabServer() routines were removed.

These routines are usually used by the window manager. Grabbing the server should be done only when really necessary, but you can of course put them back if you need them.

The example from gscreendump is probably using them to create a rubber-banding effect, since as was stated, it's using GXxor function to draw the lines.

Marco



```



#include <iostream>
#include <cstdlib>
#include <X11/Xlib.h>


// Compile: g++ mypointer.c -o my -lX11

// cc prog.c -o prog -L/usr/X11/lib -lX11
// or perhaps this (for a system with release 6 of X11):

//cc prog.c -o prog -L/usr/X11R6/lib -lX11

// On SunOs 4 systems, the X libraries are placed in /usr/openwin/lib:
// cc prog.c -o prog -L/usr/openwin/lib -lX11




/*
Ecore and Evas (XLib abstraction and canvas library) will allow you to
construct windows, place objects, buttons if needed, get / use scroll
/ warp events etc. very easily.  In Ecore/Evas, you can register
events with callbacks and do certain actions based on that. This makes
things like clicking / scrolling very simple. You could also track the
mouse movement / warp it easily. Ecore provides and event loop so you
just have to hook your application into the loop and register the
appropriate callbacks. If you feel you require a solid example or a
small tutorial then this could be the topic of our next (soon to be
held) meeting.
*/



void move_mouse_pointer(int delta_x, int delta_y)
{
// Opening and closing the display each time is not the right way to do this.
    Display *display = XOpenDisplay(0);
    XWarpPointer(display, None, None, 0, 0, 0, 0, delta_x, delta_y);
// XWarpPointer (dpy, scr->Root, scr->Root, 0, 0, scr->MyDisplayWidth, scr->MyDisplayHeight, x, y);

    XCloseDisplay(display);
}



/*
XWarpPointer(display, src_w, dest_w, src_x, src_y, src_width, src_height, dest_x,
                dest_y)
        Display *display;
        Window src_w, dest_w;
        int src_x, src_y;
        unsigned int src_width, src_height;
        int dest_x, dest_y;

Arguments

display	 Specifies the connection to the X server.
src_w	 Specifies the source window or None.
dest_w	 Specifies the destination window or None.
src_x
src_y
src_width
src_height	 Specify a rectangle in the source window.
dest_x
dest_y
*/





int GetMousePosition()
{
  Display *d;
  Window inwin;      /* root window the pointer is in */
  Window inchildwin; /* child win the pointer is in */
  int rootx, rooty; /* relative to the "root" window; we are not interested in these,
                       but we can't pass NULL */
  int childx, childy;  /* the values we are interested in */
  Atom atom_type_prop; /* not interested */
  int actual_format;   /* should be 32 after the call */
  unsigned int mask;   /* status of the buttons */
  unsigned long n_items, bytes_after_ret;
  Window *props; /* since we are interested just in the first value, which is
		    a Window id */

   char *display_name = NULL;

  /* default DISPLAY */
  d = XOpenDisplay(display_name);

  /* ask for active window (no error check); the client must be freedesktop
     compliant */
  (void)XGetWindowProperty(d, DefaultRootWindow(d),
			   XInternAtom(d, "_NET_ACTIVE_WINDOW", True),
			   0, 1, False, AnyPropertyType,
			   &atom_type_prop, &actual_format,
			   &n_items, &bytes_after_ret, (unsigned char**)&props);

  XQueryPointer(d, props[0], &inwin,  &inchildwin,
		&rootx, &rooty, &childx, &childy, &mask);
  printf("relative to active window: %d,%d\n", childx, childy);

  XFree(props);           /* free mem */
  (void)XCloseDisplay(d); /* and close the display */
  return 0;
}




int GetGlobalMousePosition()
{
char *display_name = NULL;
Display *dsp = XOpenDisplay( display_name );
if( !dsp ){ return 1; 

}

int screenNumber = DefaultScreen(dsp);

XEvent event;

/* get info about current pointer position */
XQueryPointer(dsp, RootWindow(dsp, DefaultScreen(dsp)),
&event.xbutton.root, &event.xbutton.window,
&event.xbutton.x_root, &event.xbutton.y_root,
&event.xbutton.x, &event.xbutton.y,
&event.xbutton.state);

printf("Mouse Coordinates: %d %d\n", event.xbutton.x, event.xbutton.y);

XCloseDisplay( dsp );
}







int main()
{
    /* this variable will contain the pointer to the Display structure */
    /* returned when opening a connection.                             */


    int screen_num;

    GetGlobalMousePosition();
    GetMousePosition();

    char *display_name = NULL;

    Display* display;

    /* open the connection to the display "simey:0". */
    display = XOpenDisplay(display_name);// display = XOpenDisplay("simey:0");
    if (display == NULL)
    {
        fprintf(stderr, "Cannot connect to X server %s\n", "simey:0");
        exit (-1);
    }

    char green[] = "#00FF00";
    GC green_gc;
    Colormap colormap;
    XColor green_col;


    colormap = DefaultColormap(display, 0);

    green_gc = XCreateGC(display,RootWindow(display, DefaultScreen(display)), 0, 0);
    XParseColor(display, colormap, green, &green_col);
	XAllocColor(display, colormap, &green_col);
	XSetForeground(display, green_gc, green_col.pixel);



    screen_num = DefaultScreen(display);
    XSetSubwindowMode(display,green_gc, IncludeInferiors);


    XDrawRectangle(display,RootWindow(display, screen_num), green_gc, 150, 150, 250, 250);
    //XFlush(display);

    

    int screen_height = DisplayHeight(display, DefaultScreen(display));
    int screen_width  = DisplayWidth(display, DefaultScreen(display));
    printf("This screen is (%d,%d)\n", screen_width, screen_height);

    XCloseDisplay( display );

    int delta_x =30;
    int delta_y =50;
    move_mouse_pointer(delta_x,delta_y);
    return 0;
}





```

That was helpful to me, I wanted to do that anyway, now you've saved me time  ;-))

In the meantime, I've created the GetPixel and the SetPixel function equivalents as well as the GetRValue, the GetGValue and the GetBValue Macro


SYNTAX
       int XDrawPoint(Display *display, Drawable d, GC gc, int x, int y);

       int XDrawPoints(Display *display, Drawable d, GC gc, XPoint *points,
              int npoints, int mode);


MSDN:
COLORREF SetPixel(
  __in  HDC hdc,
  __in  int X,
  __in  int Y,
  __in  COLORREF crColor
);

So mapping XDrawPoint to SetPixel:
typedef unsigned int DWORD; // on Linux, use int instead of long
typedef DWORD COLORREF;

and with 
	HWND desk = GetDesktopWindow();
	HDC dc = GetDC(desk);

you can say:
typedef Display* HWND ;
typedef Drawable HDC ;

//int SetPixel(Display *display,Drawable root_win, int x, int y, GC gc_line)
COLORREF SetPixel(HWND display, HDC root_win, int x, int y, GC gc_line)
{
    return (COLORREF) XDrawPoint(display, root_win, gc_line, x, y); 
}

The interesting thing is windows seems not to need HWND, so I think this implies there is a way to get display when you have root_win...

Or you could just make a define, and get the HWND in the define.

```

#include <iostream>
#include <cstdlib>
#include <X11/Xlib.h>
#include <X11/Xutil.h>


/*
root@ST-LAPTOP:/usr/include/X11# grep "XGetPixel" ./*
./Xutil.h:extern unsigned long XGetPixel(
./Xutil.h:#define XGetPixel(ximage, x, y) \
*/

// Compile: g++ mypointer.c -o my -lX11

// cc prog.c -o prog -L/usr/X11/lib -lX11
// or perhaps this (for a system with release 6 of X11):

//cc prog.c -o prog -L/usr/X11R6/lib -lX11

// On SunOs 4 systems, the X libraries are placed in /usr/openwin/lib:
// cc prog.c -o prog -L/usr/openwin/lib -lX11



#define GetRValue(dwColor) dwColor & 0x000000FF
#define GetGValue(dwColor) (dwColor & 0x0000FF00) >> 8
#define GetBValue(dwColor) dwColor >> 16 


int GetPixel(int x, int y)
{
    Display *dpy;
    XImage *image;
    XColor col;

    dpy = XOpenDisplay(NULL);
    image = XGetImage(dpy, DefaultRootWindow(dpy),
                      x, y, 1, 1, AllPlanes, ZPixmap);
    col.pixel = XGetPixel(image, 0, 0);
    XDestroyImage(image);

    // The XQueryColor() function returns the current RGB value for the pixel in the XColor structure and sets the DoRed, DoGreen, and DoBlue flags.
    // XQueryColor() can generate BadColor and BadValue errors. 
    // BadColor A value for a Colormap argument does not name a defined Colormap.
    // BadValue Some numeric value falls outside the range of values accepted by the request. 
    // Unless a specific range is specified for an argument, the full range defined by the argument's type 
    // is accepted. Any argument defined as a set of alternatives can generate this error.
    XQueryColor(dpy, DefaultColormap(dpy, DefaultScreen(dpy)), &col);
    // The colormap is a lookup table located on the server the pixel value is used as an index into the table.

    XCloseDisplay(dpy);

    printf("R: %03d G: %03d B: %03d\n", (int)((double) col.red/257.0), (int)((double) col.green/257.0), (int)((double) col.blue/257.0));
    return (col.red&0xff00)<<8 | (col.green)&0xff00 | (col.blue) >> 8; // = windows return value
}


int main()
{
    // this variable will contain the pointer to the Display structure
    // returned when opening a connection.
    Display* display;
    int screen_num;
    Screen *screen;
    Window root_win;
    XGCValues gc_val;

    // open the connection to the display "simey:0".
    display = XOpenDisplay(0);// display = XOpenDisplay("simey:0");
    if (display == NULL)
    {
        fprintf(stderr, "Cannot connect to X server %s\n", "simey:0");
        exit (EXIT_FAILURE);
    }

    XGrabServer(display);

    screen_num = DefaultScreen(display);
    screen = XScreenOfDisplay(display, screen_num);
    root_win = RootWindow(display, XScreenNumberOfScreen(screen));

    // Create a GC (Graphics Context) for the line
    gc_val.function           = GXxor;
    gc_val.plane_mask         = AllPlanes;
    gc_val.foreground         = WhitePixel(display, screen_num);
    gc_val.background         = BlackPixel(display, screen_num);
    gc_val.line_width         = 4;
    gc_val.line_style         = LineSolid;
    gc_val.cap_style          = CapButt;
    gc_val.join_style         = JoinMiter;
    gc_val.fill_style         = FillOpaqueStippled;
    gc_val.fill_rule          = WindingRule;
    gc_val.graphics_exposures = False;
    gc_val.clip_x_origin      = 0;
    gc_val.clip_y_origin      = 0;
    gc_val.clip_mask          = None;
    gc_val.subwindow_mode     = IncludeInferiors;

    GC  gc_line = XCreateGC(display, root_win, GCFunction | GCPlaneMask |  GCForeground | GCBackground | GCLineWidth | GCLineStyle |
                            GCCapStyle  | GCJoinStyle  |  GCFillStyle  |  GCFillRule  |  GCGraphicsExposures |
                            GCClipXOrigin |  GCClipYOrigin  |  GCClipMask  | GCSubwindowMode, &gc_val);

    // XSetForeground(display, gc_line, some_color);
    // XDrawRectangle(display, root_win, gc_line, 50, 50, 400, 400);
    for (int ix = 0; ix < 1000;++ix)
        XDrawPoint(display, root_win, gc_line, ix, 50); // SetPixel


    XFlush(display);
    XUngrabServer(display);


    XCloseDisplay( display );

    int iMyColor =  GetPixel(20,20) ;
    printf("Sole color: 0x%08X\n", iMyColor);
    printf("R: %03d G: %03d B: %03d\n", GetRValue(iMyColor), GetGValue(iMyColor), GetBValue(iMyColor));


    // printf("Sizof short: %ld\n", sizeof(unsigned short)) ; // 2 Bytes
    return EXIT_SUCCESS ;
}


```

---

### Post by pshirishreddy on 2009-11-16
how to perform left click or mouse clicks on the root screen ? the above code helped me lot thank you :D

---

### Post by WitchCraft on 2010-03-04
> **pshirishreddy said:**
> how to perform left click or mouse clicks on the root screen ? the above code helped me lot thank you :D

Pixel Aimbot ! lol works


See here
[http://fixunix.com/xwindows/91958-simulate-mouse-buttons-using-xlib.html](http://fixunix.com/xwindows/91958-simulate-mouse-buttons-using-xlib.html)
And here:
[http://www.linuxquestions.org/questions/programming-9/simulating-a-mouse-click-594576/](http://www.linuxquestions.org/questions/programming-9/simulating-a-mouse-click-594576/)

---

