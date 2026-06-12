---
title: "Ubuntu and message loops."
date: 2013-07-31
forum: Programming Talk
---

### Post by irancplusplus on 2013-07-31
In Windows API, everything is going like this:
There's a message loop. the message loop checks if there's any messages in message queue. messages like a click on an item, a keystroke from keyboard or a time message. If there's any, the message loop sends that message to an appropriate message-processing function. The loop continues checking and sending messages forever (until a it gets a close message).

This is the how windows works.

How does Ubuntu Linux work? Does it have a similar process? If so, can you give me a simple program with a message loop?

---

### Post by Tony Flury on 2013-08-01
Most Linux frameworks work in a similar way - but the specifics will depend on what GUI framework you are using - there is not a single API for windowing and mouse events like there is under MS Windows.

I know that GTK there is a function called gtk_main_loop() that you call and the events trigger the execution of the the connected handlers for each widget - I think QT and WX have a similar idea. If you use something like pygame - you have to hand write your main loop, and check for the events that and decide which handlers need to be called.

---

### Post by MG&amp;TL on 2013-08-01
> **irancplusplus said:**
> Does it have a similar process?

It depends how low-level you wish to go. Going all the way down to the X server, this is approximately what happens (X experts, I apologise in advance):

[LIST=1]
[*]A client (for most intents and purposes, a window) connects to the X server. The client uses a library for this task, usually *Xlib*, although *XCB* is now preferred. 
[*]The window manager and/or the X server sends events to the client through the X server connection. These events can be pretty much anything, and can be freely ignored or acted on by the client. 
[*]The client uses a library again to read the events from the connection, filtering those it wishes to use. 
[*]When the client decides to exit (or is killed), it disconnects from the X server. 
[/LIST]

If you want (a lot) more information, try [http://tronche.com/gui/x/xlib/events/](http://tronche.com/gui/x/xlib/events/). *Xlib* is a bit of a monster, however.

Most GUI toolkits wrap this in a manner idiomatic to the toolkit. I believe GTK+ uses signal callbacks, whereas Qt uses a signal/slot mechanism. Some simply provide a queue of pre-filtered events to process.

---

