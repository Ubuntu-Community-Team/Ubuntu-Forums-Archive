---
title: "screensaver and X11"
date: 2011-07-19
forum: Programming Talk
---

### Post by newelfik on 2011-07-19
Hello,

I would like to draw a picture in X11 for screensaver.

So I started with excelent doc : [http://tronche.com/gui/x/xlib/](http://tronche.com/gui/x/xlib/)

And try to start with simpler thing like display text. So I've written that : 

```

#include <stdio.h> 
#include <X11/Xlib.h> 
#include <stdlib.h>
#include <time.h>

#include "vroot.h"

Display *display;
Window root;
GC gc;


int main (argc, argv) 
 char   *argv[]; 
 int     argc; 
{ 
	display = XOpenDisplay (getenv ("DISPLAY"));
	if( display == NULL ){
		printf("display = NULL");
	}
	
	printf("connection number : %d\n" , ConnectionNumber( display ) );
	
	printf("height : %d\n", DisplayHeight(display , 0));
	printf("width : %d\n", DisplayWidth(display , 0));
	
	/* get the root window */
	root = DefaultRootWindow (display);
	
	gc = XCreateGC(display, root , 0 , NULL );
	
	XTextItem *text = (XTextItem*)malloc(1 * sizeof(XTextItem));
	text->chars = "Test TEST Test test TEST";
	text->nchars = 24;
	text->delta = 1;
	text->font = None;
	
	/* set foreground color */
	XSetForeground(display, gc, WhitePixelOfScreen(DefaultScreenOfDisplay(display)) );
	
	/* draw something */
	  while (1)
	    {
	      /* draw a square */
		  XDrawText(display, root , gc , 100, 100, text , 1 );


	      /* once in a while, clear all */
	      if( random()%500<1 )
	        XClearWindow(display, root);


	      /* flush changes and sleep */
	      XFlush(display);
	      usleep (10);
	    }
	
	XCloseDisplay( display );
	
	printf("OK\n");
}

```

If I set the code as a screensaver and select [Preview], it's running.. I see the text.

If I launch screensaver in real conditions, I see only black screen ...

Have you got an idea ?

---

### Post by pbrane on 2011-07-19
I would recommend that you download the xscreensaver code and have a look at how it's done.

you can get it from the repos
```

sudo apt-get source xscreensaver

```

---

