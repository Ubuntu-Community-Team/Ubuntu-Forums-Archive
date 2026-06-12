---
title: "How do you debug pygtk code?"
date: 2008-06-03
forum: Programming Talk
---

### Post by Jadd on 2008-06-03
What's the best way to debug pygtk code? In general, how would you do it?

I often get crashes when running various pygtk apps, giving me no error codes, or else output like this:
```
python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request' failed.
```
How do you go about debugging something like this?

---

### Post by OpenFish on 2008-06-21
would i be right in thinking that that is referring to a c library python is using (lots of pygtk modules intern call a bit of a c library (gnome)) if u have the source (i assume u do as it python, and u are debugging it) then u might be able to track down whats calling the library and ether the python is giving it some thing it shouldnt and not caching it or there is a bug in the c libary i would Imagen

are u only getting that line of code or are u geting some more telling u were the module is getting called

i have this problem when i give a gtk module args that are not suitable but the module dosn't check before passing it on to the c and when the c fails u get a odd message like that in stead of a nice clean python error

so fare it has always bin my folt not had one bug

---

