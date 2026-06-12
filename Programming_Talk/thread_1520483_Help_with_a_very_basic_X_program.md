---
title: "Help with a very basic X program"
date: 2010-06-29
forum: Programming Talk
---

### Post by Yes on 2010-06-29
I'm trying to learn how to program with X, and I'm running into some problems drawing in my window.  My code runs with no errors, and it does create the window but my problem is it doesn't draw any of the pixels that it's supposed to.  Here's the code:

```
#include <X11/Xlib.h> // Every Xlib program must include this

#include <stdio.h>
#include <stdlib.h>		/* getenv(), etc. */
#include <unistd.h>		/* sleep(), etc.  */

#define NIL (0)       // A name for the void pointer

/*
 * function: create_simple_window. Creates a window with a white background
 *           in the given size.
 * input:    display, size of the window (in pixels), and location of the window
 *           (in pixels).
 * output:   the window's ID.
 * notes:    window is created with a black border, 2 pixels wide.
 *           the window is automatically mapped after its creation.
 */
Window
create_simple_window(Display* display, int width, int height, int x, int y)
{
	int screen_num = DefaultScreen(display);
    int win_border_width = 2;
    Window win;

    /* create a simple window, as a direct child of the screen's */
    /* root window. Use the screen's black and white colors as   */
  	/* the foreground and background colors of the window,       */
	/* respectively. Place the new window's top-left corner at   */
  	/* the given 'x,y' coordinates.                              */
 	win = XCreateSimpleWindow(display, RootWindow(display, screen_num),
                            x, y, width, height, win_border_width,
                            BlackPixel(display, screen_num),
                            WhitePixel(display, screen_num));

  	/* make the window actually appear on the screen. */
  	XMapWindow(display, win);

  	/* flush all pending requests to the X server. */
  	XFlush(display);

  	return win;
}

GC
create_gc(Display* display, Window win, int reverse_video)
{
  	GC gc;				/* handle of newly created GC.  */
  	unsigned long valuemask = 0;		/* which values in 'values' to  */
					/* check when creating the GC.  */
  	XGCValues values;			/* initial values for the GC.   */
  	unsigned int line_width = 2;		/* line width for the GC.       */
  	int line_style = LineSolid;		/* style for lines drawing and  */
  	int cap_style = CapButt;		/* style of the line's edje and */
  	int join_style = JoinBevel;		/*  joined lines.		*/
  	int screen_num = DefaultScreen(display);

  	gc = XCreateGC(display, win, valuemask, &values);
  	if (gc < 0) {
		fprintf(stderr, "XCreateGC: \n");
  	}

  	/* allocate foreground and background colors for this GC. */
  	if (reverse_video) {
	    XSetForeground(display, gc, WhitePixel(display, screen_num));
	    XSetBackground(display, gc, BlackPixel(display, screen_num));
  	}
  	else {
	    XSetForeground(display, gc, BlackPixel(display, screen_num));
    	XSetBackground(display, gc, WhitePixel(display, screen_num));
  	}

  	/* define the style of lines that will be drawn using this GC. */
  	XSetLineAttributes(display, gc,
                     line_width, line_style, cap_style, join_style);

  	/* define the fill style for the GC. to be 'solid filling'. */
  	XSetFillStyle(display, gc, FillSolid);

	XFlush (display);

  	return gc;
}


int main(int argc, char *argv[])
{
 	Display* display;		/* pointer to X Display structure.           */
	int screen_num;		/* number of screen to place the window on.  */
  	Window win;			/* pointer to the newly created window.      */
	unsigned int display_width,
               	display_height;	/* height and width of the X display.        */
  	unsigned int width, height;	/* height and width for the new window.      */
  	char *display_name = getenv("DISPLAY");  /* address of the X display.      */
  	GC gc;			/* GC (graphics context) used for drawing    */
					/*  in our window.			     */
	
  	/* open connection with the X server. */
  	display = XOpenDisplay(display_name);
  	if (display == NULL) {
    	fprintf(stderr, "%s: cannot connect to X server '%s'\n",
            	argv[0], display_name);
    	exit(1);
  	}
	
	/* get the geometry of the default screen for our display. */
  	screen_num = DefaultScreen(display);
  	display_width = DisplayWidth(display, screen_num);
  	display_height = DisplayHeight(display, screen_num);
	
  	/* make the new window occupy 1/9 of the screen's size. */
  	width = (display_width / 3);
  	height = (display_height / 3);
  	printf("window width - '%d'; height - '%d'\n", width, height);
	
  	/* create a simple window, as a direct child of the screen's   */
  	/* root window. Use the screen's white color as the background */
  	/* color of the window. Place the new window's top-left corner */
  	/* at the given 'x,y' coordinates.                             */
  	win = create_simple_window(display, width, height, 150, 150);
	
  	/* allocate a new GC (graphics context) for drawing in the window. */
  	gc = create_gc(display, win, 0);
  	XSync(display, False);
	
  	/* draw one pixel near each corner of the window */
  	XDrawPoint(display, win, gc, 5, 5);
  	XDrawPoint(display, win, gc, 5, height-5);
  	XDrawPoint(display, win, gc, width-5, 5);
  	XDrawPoint(display, win, gc, width-5, height-5);
	
	XFlush (display);
	XSync(display, False);
	
	sleep (4);

	XCloseDisplay(display);
	
	return 0;
}
```

Any help would be much appreciated :p

---

### Post by ibuclaw on 2010-06-29
When you call XMapWindow(), make sure that you call:
```
XSync(display, False);
```
Immediately after it. ;)

Regards
Iain

---

### Post by Yes on 2010-06-30
Thanks, but that hasn't done it.  Should I be calling XMapWindow after drawing the stuff too?  Right now I just call it to make the window appear.

---

### Post by ibuclaw on 2010-06-30
> **Yes said:**
> Thanks, but that hasn't done it.  Should I be calling XMapWindow after drawing the stuff too?  Right now I just call it to make the window appear.

OIC, sorry. I should have tested that more. For me, it shows the dots every 3 in 4 attempts of running the application.

Weird...

---

### Post by Yes on 2010-06-30
Really?  They never show up for me.  I've simply copy and pasted the code from a tutorial, and nothing comes up.  Could there be something wrong with my setup, outside of the program?

e:  I tried it on another computer and it worked.  Perhaps AwesomeWm is screwing something up?

e2:  Nope, I tried it in Gnome and it still doesn't work. Not only that, but they're both running Arch, and both systems have been totally upgraded from the same repos, and then rebooted.  Yet the one still works, and the other one doesn't.  Very odd.

---

### Post by ibuclaw on 2010-06-30
> **Yes said:**
> Really?  They never show up for me.  I've simply copy and pasted the code from a tutorial, and nothing comes up.  Could there be something wrong with my setup, outside of the program?

e:  I tried it on another computer and it worked.  Perhaps AwesomeWm is screwing something up?

e2:  Nope, I tried it in Gnome and it still doesn't work. Not only that, but they're both running Arch, and both systems have been totally upgraded from the same repos, and then rebooted.  Yet the one still works, and the other one doesn't.  Very odd.

If that is the case, perhaps Unity is screwing something up too. ;)

I know various WMs need various X quirks in order to fix race conditions, rendering, etc, etc.

edit:
Putting this before XMapWindow() fixes it for me.
```

        XClassHint* ch = XAllocClassHint();
        // May want to check that ch is not NULL here.
        ch->res_name = "window";
        ch->res_class = "test";
        XSetClassHint(display, win, ch);
        XFree(ch);

```

---

### Post by Yes on 2010-07-01
Thanks very much, but it seems I'm missing something?  I get the compile error "XClassHint is undefined".

e:  Nevermind, I had to include X11/Xutil.h, unfortunately I still don't see anything.  Hmm, I'm working on another project for now, when I have some more time I'll take a poke at it.  Thanks!

---

