---
title: "Include files in non-standard directories?"
date: 2009-11-27
forum: Programming Talk
---

### Post by pmunly on 2009-11-27
Ok, first off I'm just getting back into C/Gtk (it's been about 2 years) and messing around with SDL a bit, so I'm working on a very simple SDL/Gtk demo to get the feel for things.  My problem is that it appears that my Ubuntu Netbook Remix 9.10 install has a *lot* of include files in what I believe are non-standard locations... mainly those upon which gtk and gdk depend:

#include <gtk/gtk.h>
#include <gdk/gdk.h>

should be found in /usr/include/gtk and /usr/include/gdk at least from my understanding.  Instead they're both in /usr/include/gtk-2.0/gtk and /usr/include/gtk-2.0/gdk, which is not really a problem; it's easy making a symbolic link to put them in the "right" spot.  So that's what I did.  After attempting to compile again, I received somewhere in the range of 6000 errors due to other header files "not found" where gtk.h and gdk.h thought they should be (and the *-dev packages are installed).  So I guess I'm wondering if I've completely forgot/missed something here, or if there's something else I should be doing?  

Any help would be much appreciated.  And yes, I realize trying to write code on a Netbook is a bit crazy. :)

---

### Post by dwhitney67 on 2009-11-27
> **pmunly said:**
> ...it's easy making a symbolic link to put them in the "right" spot...
Undo what you did in this step; that was the "wrong" thing to do!

For GTK+, it supports the package configuration, or pkg-config, facility.

Header file paths and other special compiler options, are available via the --cflags option.  For linker paths and options, the --libs option is used.

Thus to compile/link a simple program:
```

gcc `pkg-config --cflags gtk+-2.0` -c MyProg.c
gcc MyProg.o `pkg-config --libs gtk+-2.0` -o myprog

```
This topic has been discussed ad nauseum in this forum; thus if you do not comprehend what I have stated above, then happy searching using the forum search tool.

P.S.  If you are developing in C++, then replace the 'gcc' shown above with 'g++'.

---

### Post by pmunly on 2009-11-27
That did the trick, thanks for the help!  Time to brush up on pkg-config I guess :)

---

