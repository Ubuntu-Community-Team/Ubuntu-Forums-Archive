---
title: "Xlib question, XSelectInput from two or more windows"
date: 2010-04-08
forum: Programming Talk
---

### Post by Nathan-1000 on 2010-04-08
Hi guys,

I'm writing an application launcher at the moment. The application launcher side of things is done using imlib2 and Xlib and is completely finished.

I want to be able to get input from the root window, and the window I'm drawing to, so I know when a user has clicked something in my window, as well as when a separate window has been opened or destroyed.

I've had some success by running two loops in separate threads (one in the main program, the other in it's own thread), but when I open another application, the program crashes. I'm sure this is because X11 isn't thread safe.

So, is there any easy way to get events from both windows?

---

### Post by NathanB on 2010-04-08
There sure is!  Xlib is just a set of generic wrapper functions around a set of socket calls.  So, if you use raw sockets (instead of Xlib) to communicate with those windows, you'll get a more direct and fine-tuned interface to them.

---

