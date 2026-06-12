---
title: "Key Combination with XLib and XGrabKey function"
date: 2008-11-11
forum: Programming Talk
---

### Post by xdd123www on 2008-11-11
Hi ,

Can anyone help me with XLib and XGrabKey function?
I want to add key combination to my application .
but it didn't work.

code:
--------------------------
    Window root ;
    XEvent event;
   
    Display *dpy = XOpenDisplay(0);
   
    if(!dpy) 
    {
        printf("Error for openning display.\nExit..\n");
        return ;
    }
   
    root = DefaultRootWindow(dpy);

    KeyCode key = XKeysymToKeycode(dpy,XK_F9 ) ;


    	unsigned int mod = 0 ;
	mod = mod | ControlMask ;

	XGrabKey(dpy, key ,  mod , root,True, GrabModeAsync, GrabModeAsync);

    for( ; ; )
    {

            XNextEvent(dpy, &event);
            if(event.type == KeyPress && event.xkey.keycode == key ) //
        {
            // do sth...           
            }
        }

    XAllowEvents(dpy,AsyncKeyboard,CurrentTime);
    XUngrabKey(dpy, key, AnyModifier, root);
    XSync(dpy,false);

-----------------------

How should I use it to get it work?

---

### Post by xdd123www on 2008-11-11
but it work well like this :

XGrabKey( dpy, XKeysymToKeycode(dpy,XK_F9 ) , AnyModifier , root,true, GrabModeAsync, GrabModeAsync ) ;


when i used 'ControlMask' ,
it seems that ,
"XNextEvent(dpy, &event);" didn't copy any event from queue .



Any help, much appreciated.

---

