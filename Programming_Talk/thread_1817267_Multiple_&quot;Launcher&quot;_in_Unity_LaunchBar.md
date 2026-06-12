---
title: "Multiple &quot;Launcher&quot; in Unity LaunchBar"
date: 2011-08-03
forum: Programming Talk
---

### Post by Darksquall57 on 2011-08-03
Hi everybody :D,

I try to open a simple window in C++ by using XOpenDisplay() and XCreateSimpleWindow(). The problem is when the window opens, many entries appears in the Unity LaunchBar.

Here is my code :
```

#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/Xos.h>
#include <X11/Xatom.h>
#include <X11/keysym.h>

int main()
{

    Display *dis;
    Window win;

    dis = XOpenDisplay(NULL);
    win = XCreateSimpleWindow(dis, RootWindow(dis, 0), 1, 1, 500, 500, 0, BlackPixel (dis, 0), BlackPixel(dis, 0));
    XMapWindow(dis, win);
    XFlush(dis);
    /*Sleep 5 seconds before closing.*/
    sleep(5);

    return 0;
}

```And here is the problem : 

[ATTACH]199146[/ATTACH]

How can I have just one entry ? Please help me !:(

PS : When I put my mouse on it, I see the name is Launcher. How can I change this name ?

---

### Post by Darksquall57 on 2011-08-03
I resolved my problem.

I used XCreateSimpleWindow() like this :

```


#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/Xos.h>
#include <X11/Xatom.h>
#include <X11/keysym.h>
#define KEYMAX 2048

int main()
{
    Display *dp;
    GC copygc,andgc,orgc,xorgc;
    int usedcolors;
    unsigned char mymap[768];
    int screen;
    Window wi;
    int fontbase,fontysize;
    XImage *myimage;
    char *imageloc;
    XEvent event;
    XKeyEvent *keyevent;
    XButtonEvent *buttonevent;
    XMotionEvent *motionevent;
    XExposeEvent *exposeevent;

    Pixmap artwork,artmask,bgframe,storeage;
    long map2[256];
    Colormap cmap,mycolormap;
    unsigned char fmap[128];
    int buttonstate=0,buttondown=0;
    int mxpos,mypos;

    int pressedcodes[KEYMAX],downcodes[KEYMAX],numpressed,numdown;

    XFontStruct *afont;
    XGCValues values;
    XSizeHints *sizehints;
    XWMHints *wmhints;
    XClassHint *classhints;
    XTextProperty windowName;
    XTextProperty iconName;
    char *title = "Icon Name";
    char *title1 = "Application Class Name";
    int depth;

    dp=XOpenDisplay(0);
    if(!dp)
    {
        printf("Cannot open display\n");
        exit(1);
    }
    screen=XDefaultScreen(dp);
    cmap=DefaultColormap(dp,screen);
    depth = DefaultDepth(dp, screen);
    wi=XCreateSimpleWindow(dp,RootWindow(dp,screen),20,20,640,480,0,0,0);

    wmhints = XAllocWMHints ();
    /* Various window manager settings */
    wmhints->initial_state = NormalState;
    wmhints->input = True;
    wmhints->flags = StateHint | InputHint;


    /* Set the class for this program */
    classhints = XAllocClassHint ();
    classhints->res_name = title1;
    classhints->res_class = title1;

    /* Setup the max and minimum size that the window will be */
    sizehints = XAllocSizeHints ();
    sizehints->flags = PSize | PMinSize | PMaxSize;
    sizehints->min_width = 640;
    sizehints->min_height = 480;
    sizehints->max_width = 640;
    sizehints->max_height = 480;
    /* Create the window/icon name properties */
    if (XStringListToTextProperty (&title, 1, &windowName) == 0)
    {
        fprintf (stderr, "X: Cannot create window name resource!\n");
        exit (3);
    }
    if (XStringListToTextProperty (&title1, 1, &iconName) == 0)
    {
        fprintf (stderr, "X: Cannot create window name resource!\n");
        exit (3);
    }

    /* Now set the window manager properties */
    XSetWMProperties (dp, wi, &windowName, &iconName, 0, 0, sizehints, wmhints, classhints);
    XFree ((void *) wmhints);
    XFree ((void *) classhints);
    XFree ((void *) sizehints);

    XMapWindow(dp,wi);
    XSelectInput(dp,wi,KeyPressMask | KeyReleaseMask | ButtonPressMask | ButtonReleaseMask | PointerMotionMask | ExposureMask | FocusChangeMask);

    XFlush(dp);

    sleep(10);

}


```

---

