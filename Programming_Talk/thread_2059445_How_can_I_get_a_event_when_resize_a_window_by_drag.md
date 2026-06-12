---
title: "How can I get a event when resize a window by drag its frame?"
date: 2012-09-18
forum: Programming Talk
---

### Post by cnzfdsc on 2012-09-18
I used Xlib for my program.
and I used these masks below :
::XSelectInput( (Display*) mDisplay, (Window) mWindow, ExposureMask | ButtonMotionMask | ButtonPressMask | ButtonReleaseMask | EnterWindowMask | LeaveWindowMask | FocusChangeMask | KeyPressMask | KeyReleaseMask | ResizeRedirectMask | StructureNotifyMask );
 
And I can not get a ConfigureNotify or ResizeRequest when I drag the frame to resize the window.

---

