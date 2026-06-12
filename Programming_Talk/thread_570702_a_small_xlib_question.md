---
title: "a small xlib question"
date: 2007-10-08
forum: Programming Talk
---

### Post by rksk16it on 2007-10-08
Hello friends :)
Before presenting my question, i would like to ask if anyone knows about any forum / mailing-list where i can post my xlib questions , if u do know one, pls present a link, that would be really nice :)

My problem is :-

What i want :- 
i want to make a program that sends a particular sequence of keyboard events to any application i want.

What i tried and found :-
On searching the manual i found a function called XSendEvent()
[(link-to-manual)]("http://tronche.com/gui/x/xlib/event-handling/XSendEvent.html"). this function can send event to other windows, so as expected (obviously) it takes an argument (2nd one) "w" which represent the window-ID of the target window. The manual says it can be given to special values "PointerWindow" and "InputFocus", so just out of curiousity i tried this program :-

```

#include <X11/Xlib.h>
#include <unistd.h>

int main(int argc, char **argv)
{
	Display *dpy = XOpenDisplay(NULL);

	sleep(5); // This gives me time to take my pointer anywhere.

	std::cout<<PointerWindow;          // this always prints 0
	std::cout<<InputFocus<<endl;       // this always prints 1
	std::cout<<DefaultRootWindow(dpy); // this prints a number(342)

	XCloseDisplay(dpy);
}
```

i found that "PointerWindow" and "InputFocus" to always print 0 and 1 respectively, but i want to know the window-ID of the destination window, so i can use it in XSendEvent().

i searched internet and found a program called "xvkbd", a virtul keyboard for X and downloaded its source and tried to read source (i tried to find XSendEvent() in it.) The source code is fairly too complicated for me (i have just started to learn Xlib) and i cant find what i want in that.

Finally :-
I decided to post this question here, since i was unable to find any forum for XLib questions.

My Question Summarized :-
Is there any way using Xlib to determine the window-ID of any arbitrary window (by selecting it, or by pointer in it, or whatever...). There should be, otherwise how the programs like "xvkbd" work ? :P

Thanks in advance (and again, if u know any Xlib forum/mailing list , pls tell me) :)

---

### Post by j_g on 2007-10-08
I've written a few X Windows apps, and also successfully used XSendEvent, so I think that I can help you out a little here.

Under the Windows OS, a windows handle (ie, HWND) is an entity on its own. It doesn't require any other handle in order to conclusively identity the window. So for example, you can locate a window by calling FindWindow() (to get the HWND of the window), and then send it a message using SendMessage().

Under X Windows, a window ID is a numeric value that _must_ be associated with a certain display handle. A window ID without a display handle is meaningless. For example, if you open one display and create a window on it, you may get a window ID of 0. If you leave this display/window open, and then open another display and create a window on it, this second window may also get an ID of 0. Now you have two different windows with the same ID. What is the difference? Each window belongs to a different display handle. (I haven't looked over the X windows sources, but I suspect that the window ID is simply some numeric value used to look up a "window struct" that is stored somewhere in a list referenced via the display handle). That's why XSendEvent must be passed both a display handle and a window ID. You must pass the appropriate display handle (to which your desired window belongs), and then also the ID of the desired window. _Only then_ will XSendEvent know to which window you want the event sent. You can't pass a 0 display handle, and then expect XSendEvent to know which window you want. (A 0 display handle to XSendEvent does _not_ imply "the default display". It must be an actual, non-zero value).

If your app is single-threaded, the best approach is to save both your display handle, and window ID, in global variables, so your function that does the XSendEvent can reference them. Here's a short, untested X Windows app to demonstrate what I mean. It sends my window a ClientMessage of my own design (ie, a custom ClientMessage with an atom arbitrarily named "MyAtom"). NOTE: Error checking is omitted. Also note that if you want your message loop to be informed of ClientMessage events you generate with XSendEvent, you need to tell X Windows you want those events via XSelectInput's StructureNotifyMask.

```
#include <X11/Xlib.h>
#include <X11/Intrinsic.h>
#include <X11/Xutil.h>
#include <X11/Xos.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

Display *MyDisplay;
Window MyWindow;
Atom MyAtom;

static void send_event(void);
{
   XClientMessageEvent xevent;
 
   // Send a ClientMessage
   xevent.type = ClientMessage;

   // Use the Atom we got for our custom message
   xevent.message_type = MyAtom;

   // I don't really use these fields, but here's an example
   // of setting them
   xevent.format = 32;
   xevent.data.l[0] = 0;

   // Send the ClientMessage event
   XSendEvent(MyDisplay, MyWindow, 0, 0, (XEvent *)&xevent);
}

int main (int argc, char *argv[])
{
   Atom wm_delete_window;
   Atom wm_protocols;

   // Open screen/window
   MyDisplay = XOpenDisplay(0);
   MyWindow = XCreateSimpleWindow(MyDisplay, DefaultRootWindow(MyDisplay),
     50, 50, 500, 400, 0, BlackPixel(MyDisplay, DefaultScreen(MyDisplay)),
     WhitePixel(MyDisplay, DefaultScreen(MyDisplay)));

   // We want to know about the user clicking on the close window button
   wm_delete_window = XInternAtom(MyDisplay, "WM_DELETE_WINDOW", 0);
   XSetWMProtocols(MyDisplay, MyWindow, &wm_delete_window, 1);
   wm_protocols = XInternAtom(MyDisplay, "WM_PROTOCOLS", 0);

   // We want to know about ClientMessages
   XSelectInput(MyDisplay, MyWindow, StructureNotifyMask);

   // Display the window
   XMapWindow(MyDisplay, MyWindow);

   // Get an Atom to use for my custom message. Arbitrarily name the atom
   // "MyAtom"
   Atom = XInternAtom(MyDisplay, "MyAtom", 0);

   // Send my window my custom ClientMessage event
   send_event();

   // Do the message loop
   for (;;)
   {
      XEvent event;

      XNextEvent(MyDisplay, &event);
      switch (event.type)
      {
         case ClientMessage:
         {
            XClientMessageEvent *evt;
		
            evt = (XClientMessageEvent *)&event;

            // User wants to close the window?
            if (evt->message_type == wm_protocols && evt->data.l[0] == wm_delete_window) goto out;

            // Is it my custom message?
            if (evt->message_type == MyAtom)
            {
               // Here I would do something about my custom message
            }
         }
      }
   }
out:

   XCloseDisplay(MyDisplay);
   return(0);
}
```

Here's a couple other points. The display handle is not good across threads. (Argh! I so much prefer the MS Windows way of doing things). Therefore, if you launch a separate thread which does the XSendEvent, then you need to specifically open the desired display to get a handle good for that thread. Here's a threadsafe version of send_event:

```
static void send_event(void);
{
   XClientMessageEvent xevent;
   Display dpy;
 
   // Display handles are not good across threads, so we have
   // to open the desired display. We want the default display here
   dpy = XOpenDisplay(0);

   // Send a ClientMessage
   xevent.type = ClientMessage;

   // Use the Atom we got for our custom message
   xevent.message_type = MyAtom;

   // I don't really use these fields, but here's an example
   // of setting them
   xevent.format = 32;
   xevent.data.l[0] = 0;

   // Send the ClientMessage event
   XSendEvent(dpy, MyWindow, 0, 0, (XEvent *)&xevent);

   // Close the display now that the event is sent
   XCloseDisplay(dpy);
}
```

Here's another potentially useful thing. If you want to get the underlying window ID of a GTK window, in order to use it with XSendEvent, here's how to do it.

```
MyWindow = GDK_WINDOW_XID(GTK_WIDGET(MyGtkWindowHandle)->window);
```

But you also need to make a "GDK version" of your X Windows Atom, and attach some function in your GTK app to be called when you XSendEvent your ClientMessage.

```
gatom = gdk_x11_xatom_to_atom(MyAtom);
gdk_add_client_message_filter(gatom, my_handler, 0);
```

---

### Post by rksk16it on 2007-10-09
Thanks a lot :)
The fact that diferent apps maybe using different display IDs was something i missed. 

I saw your examples about XSendEvent(), but you called them with arguments of display-IDs and window-IDs of only those displays and windows which you yourself created in your app.

What i want is, for example i am running a game and i need to press the button "3" repeatedly for half-hour (this is real situation :P), and i want to make a program that somehow get all the necessary information about that game-window (its display-ID, window-ID, etc..) and then use XSendEvent repeatedly to send it keyboard events, and i can do some other work ;)

The main problem i am facing is i **haven't** created the game-window, so initially i dont have necessary info with my program about that window. The way to acquire that information is actually the root of all my problems.

Thanks again, btw...your point regarding threads is something i didn't knew, so though you haven't completely solved my problems, you prevented me from running into some of them in future :D

---

### Post by ron_wg on 2010-06-17
I have found a method.  Being a nascent C programmer and new to xlib I started with Muhammad A Muquit's grabc.  Rather than waiting for a mouse click, I xwarppointer to the pixel of interest then xquerypointer to find the window id under the pointer (and containing the pixel of interest).  This gives the necessary window for the XImage functions to work.  Results are reported in rrr,ggg,bbb format on stdout.  You can grab that in a bash script using a line like:

    pix=`pixcolor $(($currx)) $(($curry))`

Because this is for my own use (to play a game) I don't bother putting the pointer back where it was...
        if (argc < 3 || argc > 3)
     {
            (void) fprintf (stderr,"Wrong number of arguments\n");
            exit(2);
        }
        x=atoi(argv[1]);
        y=atoi(argv[2]);
        display=XOpenDisplay((char *) NULL);
        cmap=DefaultColormap(display,DefaultScreen(display));
        


        XSetErrorHandler(MXError);

        if (display == (Display *) NULL)
        {
            (void) fprintf (stderr,"Failed to open local DISPLAY!'n");
            exit(1);
        }
        
        XWarpPointer (display, None, XRootWindow(display,DefaultScreen(display)), 0, 0, 0, 0, x, y);

        status=getWindowColor(display,&color,x,y);

         if (status == True)
        {
            XQueryColor(display,cmap,&color);
            r=(color.red >> 8);
            g=(color.green >> 8);
            b=(color.blue >> 8);
            (void) fprintf(stdout,"%s%d,%d,%d%s\n","",r,g,b,""); 
            (void) fflush(stdout);
        }
        else
        {
            (void) fprintf (stderr,"Failed to grab color!\n");
        }
        return (0);

---

### Post by ron_wg on 2010-06-17
Opps - only half the necessary code...  here's the other part:

static int getWindowColor(Display *display,XColor *color,int x,int y)
{
    Window
        root_window,
        target_window,
        focus,
        root_ret,
        child_ret;
        
    int
        revert_to,
        root_x,
        root_y,
        win_x,
        win_y;
         
     unsigned int
        mask_ret;

    XImage
        *ximage;

    Status
        status;
 
    root_window=XRootWindow(display,DefaultScreen(display));

    if ((XQueryPointer (display, root_window, &root_ret,
               &child_ret, &root_x, &root_y, &win_x,
               &win_y, &mask_ret)))
    {
      if (child_ret == (Window) NULL)
      {
        target_window=root_ret;

      }
      else
      {
        target_window=child_ret;
      }
    }
    else
    {
      target_window=XRootWindow(display,DefaultScreen(display));
    }

    if (target_window == (Window) NULL)
    {
        return (False);
    }
    ximage=XGetImage(display,target_window,x,y,1,1,AllPlanes,ZPixmap);
    XInitImage (ximage);

    if (ximage == (XImage *) NULL)
    {
        return (False);
    }

    color->pixel=XGetPixel(ximage,0,0);
    XDestroyImage(ximage);
    return (True);
}

---

### Post by soltanis on 2010-06-18
Code tags please.

---

### Post by garikyes on 2010-08-06
Hi guys,

I want to launch virtual keyboard application when focus is set on a line-edit widget in any running application. But the problem is that I don't have the source codes of the running applications.  Is that possible to do e.g. using Xlib API?

Any help will be much appreciated.

---

### Post by ron_wg on 2010-08-08
> **soltanis said:**
> Code tags please.


Sorry - new to the forum.. . don't know about code tags

---

