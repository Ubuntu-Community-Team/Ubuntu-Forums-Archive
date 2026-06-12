---
title: "Getting the list of running programs ( for a panel-like application )"
date: 2009-05-27
forum: Programming Talk
---

### Post by veverica17 on 2009-05-27
I am trying to make a simple panel ( like bmpanel or tint2 for example ) and I need a way to get the list of running applications.
I am working with qt4, and I know a little bit of xlib. It would be great if someone could point me to some tutorial or documentation...

It would be also great to know how to minimize and maximize windows, how to kill them, and other tasks that a normal panel does big_smile

i think i should use some xlib function( atoms maybe ), but i didnt found anything useful , i have the source code of bmpanel but its worth nothing without a good documentation ... can someone please point me to one... ( maybe there is some function in qt4.5 that can help me ? )

---

### Post by crdlb on 2009-05-27
For gtk+ you would use libwnck, which does exactly what you're after. I believe KDE has a similar library that is used by their taskbar and pager, but I don't know its name offhand. If you don't want to depend on that part of KDE, then I guess you're stuck with XLib. Your best bet for using XLib is to find a good example, either in one of those two libraries or in another minimal panel (you really don't want to use XLib if you can avoid it).

You'll want this document too, but it doesn't cover everything, only stuff that was introduced in the EWMH spec:
```
http://standards.freedesktop.org/wm-spec/wm-spec-latest.html
```

---

### Post by lensman3 on 2009-05-28
The "ps ax" command?  You would have to get the "ps" command code and look to see which kernel data structures it looks through.  It may parse the /proc/kcore file which is a map of kernel memory.  Do a "man 5 proc",  this man page has all the info on kernel pid status.

Hope this helps.

---

