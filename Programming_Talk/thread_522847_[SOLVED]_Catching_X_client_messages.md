---
title: "[SOLVED] Catching X client messages"
date: 2007-08-11
forum: Programming Talk
---

### Post by apetresc on 2007-08-11
Hello, everyone. I'm trying to get my feet wet with some Linux/OSS programming by fixing some bugs in packages I use all the time. At the moment I have this X application (raw X, doesn't use GTK or Qt or anything like that) that spawns a subprocess when it starts. However, if you close the X application with anything other than the program's "Quit" button, like the X "Close" button in the window manager, the subprocess is not stopped and continues running ad infinitum, taking up a lot of resources in the process. I essentially want to catch the event of the user clicking the "X" button, so I can close it properly.

At first I naively thought that X would simply send a SIGTERM signal when the user closed the window. So I registered a SIGTERM handler in main():
```
1839     // Register SIGTERM callback
1840     struct sigaction sa;
1841     sa.sa_handler = handler;
1842     sa.sa_flags = 0;
1843     sigaction(SIGKILL, &sa, NULL);
1844     puts("Registered sigkill handler");
```
where "handler" is simply:
```
1865 void handler(int status) {
1866         puts("In the handler function");
1867         exit(EXIT_SUCCESS);
1868 }
```
If I use "kill -TERM", then the handler works, and I see the "In the handler function" output. But it doesn't get called at all when closing the X window, so I figured some other type of mechanism was being used. So I looked up the comp.windows.x FAQ and found something that looked promising:
[quote=comp.windows.x FAQ Question 188]188 ) How do I catch the "close window" event to avoid "fatal IO error"?

	Several windows managers offer a function such as f.kill or f.delete
which sends a message to the application that it should delete its window;
this is usually interpreted as a shutdown message.
	The application needs to catch the WM_DELETE_WINDOW client message.
There is a good example in the xcalc sources in X11R5.
	Motif-based applications should in addition set the resource
XmNdeleteResponse on the top-level shell to XmDO_NOTHING, whether they are
using the Motif window manager or not.
	If the application doesn't handle this message the window manager may
wind up calling XKillClient, which disconnects the client from the display and
typically gives an Xlib error along the lines of "fatal IO error 32 (Broken 
pipe)".[/quote]

However, I'm not sure what "catch the WM_DELETE_WINDOW client message" entails, and Google'ing hasn't helped me. I checked the source of xcalc as they said, but I found nothing helpful there. The only reference to WM_DELETE_WINDOW was here:
```
146     dpy = XtDisplay(toplevel);
147     wm_delete_window = XInternAtom(dpy, "WM_DELETE_WINDOW", False);
148     (void) XSetWMProtocols(dpy, XtWindow(toplevel), &wm_delete_window, 1);
```
But I don't really understand what that does.


I'm hoping one of the gurus here can help me out :) I have little (read: none) experience with X, so please use simple language :o . Thanks in advance!

---

### Post by Airr on 2007-08-11
> **AdrianP said:**
> 
However, I'm not sure what "catch the WM_DELETE_WINDOW client message" entails, and Google'ing hasn't helped me. I checked the source of xcalc as they said, but I found nothing helpful there. The only reference to WM_DELETE_WINDOW was here:

```
 
dpy = XtDisplay(toplevel);
wm_delete_window = XInternAtom(dpy, "WM_DELETE_WINDOW", False);
(void) XSetWMProtocols(dpy, XtWindow(toplevel), wm_delete_window, 1);

```But I don't really understand what that does.


I'm hoping one of the gurus here can help me out :) I have little (read: none) experience with X, so please use simple language :o . Thanks in advance!


Basically, you create the event via XInternAtom and  register it via XSetWMProtocols.

What you need to do next is catch it in your event loop, via the ClientMessage event. 

When you receive the ClientMessage event, you then check the value in Xevent.data, and if it equals wm_delete, you exit the loop.

You should have XDestroyWindow and XCloseDisplay as the next two commands immediately following your event loop, with an exit(0) after that (not sure about the exit, C's not my main language).

{EDIT} You also, if you haven't done so already, need to register the ClientMessage event with you main window via XSelectInput.

HTH,

AIR.

---

### Post by apetresc on 2008-02-11
> **Airr said:**
> Basically, you create the event via XInternAtom and  register it via XSetWMProtocols.

What you need to do next is catch it in your event loop, via the ClientMessage event. 

When you receive the ClientMessage event, you then check the value in Xevent.data, and if it equals wm_delete, you exit the loop.

You should have XDestroyWindow and XCloseDisplay as the next two commands immediately following your event loop, with an exit(0) after that (not sure about the exit, C's not my main language).

{EDIT} You also, if you haven't done so already, need to register the ClientMessage event with you main window via XSelectInput.

HTH,

AIR.

Could you (or anyone else) please expand on this? I have no raw X-server programming experience whatsoever so the way to accomplish things like registering ClientMessage events is a mystery to me.

Any documentation to guide the way would be greatly appreciated also :)

Thanks!

---

### Post by apetresc on 2008-02-11
Okay, an update: I've successfully registered the WM_DELETE_WINDOW event using

```
    atomKill = XInternAtom(XtDisplay(player->shellWidget), "WM_DELETE_WINDOW", False);
    XSetWMProtocols(XtDisplay(player->shellWidget), XtWindow(player->shellWidget), &atomKill, 1);
```
I know this is correct because XSetWMProtocols returned a non-zero exit status, and now hitting the "X" button in the window manager does *not* close the program anymore. This is good!
But now how do I register an actual handler for this event, one that can do the required cleanup and then exit as planned.

Airr said something about ClientMessages in the event loop, but this app just uses
```
    CreatePlayerWindow();
    
    XtAppMainLoop(appContext);

    return 0;
```
ClientMessage is not mentioned anywhere.

Any more tips? Thanks :)

---

### Post by stroyan on 2008-02-11
> **Airr said:**
> 
{EDIT} You also, if you haven't done so already, need to register the ClientMessage event with you main window via XSelectInput.

The ClientMessage events don't need to be selected with XSelectInput.
They are special.  You get them without asking for them.

---

### Post by stroyan on 2008-02-11
Ah.  I see that the application is using Xt and not plain Xlib.
You can set up a callback function for ClientMessage events with a call to XtAddEventHandler.
```
XtAddEventHandler(toplevel, NoEventMask, True, handle_wm_messages, NULL);
```
Have a look at this patch for a debian package to see a very similar change to fix a different Xt based application.
[http://lists.debian.org/debian-qa-packages/2005/01/msg00152.html](http://lists.debian.org/debian-qa-packages/2005/01/msg00152.html)

---

### Post by apetresc on 2008-02-12
Bingo! With a bit of help from Xlib man pages, Google Code search, and Stroyan's advice, it's working! gnushogi is finally fixed after several years in the Ubuntu repository in a very broken state.

Thanks, guys! :)

---

