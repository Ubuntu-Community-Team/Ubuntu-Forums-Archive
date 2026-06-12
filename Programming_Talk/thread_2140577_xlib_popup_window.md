---
title: "xlib popup window"
date: 2013-04-30
forum: Programming Talk
---

### Post by thedardanius on 2013-04-30
So i coded a popup window with xlib.
Simply a window with override set to true, so window manager wont give my window any borders. (my reasson to do so)
I namely want a custom window design, thats why.
The problem is: im reasonable new to xlib, and I havent got the faintest idea of how to work further. My problems:
- It doesnt show up in the left bar, while normal programs do show up as running.
I does however show in process manager, system monitor.
- I want it to iconify the window when focus is gone, but that doesnt work, so i use unmap. but after that, icant get the window back to focus any more!!!
- Apparantly, you have to use atoms to give the program a custom icon and custom pointer texture. How to to that?!?!?

Im a windows programmer, now learning to program on linux.

---

### Post by xytron on 2013-05-04
> **thedardanius said:**
> So i coded a popup window with xlib.
Simply a window with override set to true, so window manager wont give my window any borders. (my reasson to do so)
I namely want a custom window design, thats why.
The problem is: im reasonable new to xlib, and I havent got the faintest idea of how to work further. My problems:
- It doesnt show up in the left bar, while normal programs do show up as running.
I does however show in process manager, system monitor.
- I want it to iconify the window when focus is gone, but that doesnt work, so i use unmap. but after that, icant get the window back to focus any more!!!
- Apparantly, you have to use atoms to give the program a custom icon and custom pointer texture. How to to that?!?!?

Im a windows programmer, now learning to program on linux.


If you wish for your app to be iconofy you'll need to create a pixmap for the app and then use the function 
XSetStandardProperties() like this;


XSetStandardProperties(display,		               window, 
			       title,
            		       title, 
			       icon_pixmap,
			       NULL, 
			       0, 
			       NULL); 


Also just a few comments from what I've seen of your posts.  

You'll find that examples and forums on xlib will be rather limited. Not many people use xlib as most programmers prefer a toolkit such as GTK or QT etc..

Xlib and the X Window system is not a bad system I actually think it's quite amazing what its creators accomplished, but it is a somewhat complicated system to get to know at first,  it takes some time.

If you still choose to use it you know by now that you will have to implement every functionality yourself Xlib only gives you the tools to do it.  Be prepared for a lot of work and time to be spent.

---

