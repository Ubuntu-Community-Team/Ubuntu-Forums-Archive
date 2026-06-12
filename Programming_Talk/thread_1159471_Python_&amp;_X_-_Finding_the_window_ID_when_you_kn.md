---
title: "Python &amp; X - Finding the window ID when you know the name of it"
date: 2009-05-14
forum: Programming Talk
---

### Post by JordyD on 2009-05-14
I've been trying to create a program that sends key events to certain windows based on a file full of instructions (parsing the file and translating the key names into key codes takes the bulk of the program), but unfortunately, I can find no way of finding the window ID to send the keys to.

Does anybody know of something I can use to do this? I found something through Google, but it didn't seem to be more than a command-line tool.

Thanks,
Jordy

---

### Post by NathanB on 2009-05-14
You did not specify which binding you are using, but if that binding is a wrapper around C's Xlib, then you can use "XGetWindowAttributes()" to get the window ID.

[http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming-2.html#window_ops_get_attrs](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming-2.html#window_ops_get_attrs)

If the binding makes its own socket calls to communicate with X, you will probably have to dig into the protocol to find a way to get the window IDs.

[http://en.wikipedia.org/wiki/X_Window_System_core_protocol](http://en.wikipedia.org/wiki/X_Window_System_core_protocol)

---

