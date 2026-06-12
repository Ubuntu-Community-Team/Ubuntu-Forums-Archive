---
title: "Question about x11?"
date: 2007-06-26
forum: Programming Talk
---

### Post by Ali Imran on 2007-06-26
I am not a newbie to programming in C/C++.
I have written a GUI building library (called RAD C++) for win32 systems and its own IDE, since it is GUI library so, as far I read I have to use xlib for linux, now I want to port my library to linux, and my questions are:

1. If I program using Xlib, will this be fully acceptable by compilers on ubuntu as well as other *nix compilers?
2. Does xlib provide full set of widgets, e.g. listview, treeview, guage, etc ? any list ?
3. Rightnow am on windows, can anyone give me way to configure cygwin to compile xlib based programs being on windows ?

Will be waiting for kind responses.


regards

---

### Post by geraldm on 2007-06-27
It is better to use an X toolkit, rather than program using xlib and X libs.
A toolkit allows greater use by abstracting away X.  There are cross-platform
toolkits, and I would encourage you to find one and use it.  Some are
fox(fox-toolkit.org), wxWidgets, gtk, qt, and many more.  
The widgets you are seeking are not in xlib; they are found in the 
toolkits.

best regards,
Gerald

---

### Post by moma on 2007-06-27
As **Geraldm** told there are many X Window System (or X11) toolkits around; 
[XT Toolkit intrinsicks]("http://en.wikipedia.org/wiki/X_Toolkit") (yes it sucks),  GTK2,  wxWidgets, GnuStep, Lesstif (=free motif equivalent), Xforms,  FLTK,  TCL/TK and Fox-toolkit.

[ And let's not forget OLPC's [sugar GUI and its hippocanvas ]("http://wiki.laptop.org/go/Sugar") widgettery ]

You can easily download them and study the code. Read also: [http://freshmeat.net/articles/view/928/](http://freshmeat.net/articles/view/928/)
The Trolltech's QT-toolkit is commercial but it can be used freely in GPL(non closed-source) projects.

Maybe you can build your own widget classes on GTK2 or QT?

Notice also that wxWidgets (on Unix/Linux) can be compiled using either native X11 or GTK widgets. You decide it during configuration of the wxWidgets' source. (./configure --help will tell you more).
----

But I want to make you decision slightly more complicated. I want you to 

**Drop Xlib for XCB:**
The [Xlib]("http://lesstif.sourceforge.net/doc/Xlib/spec/xlib.html") library is very old, huge pile of code.  XCB is a project that is now replacing the old XLib library. XCB is much faster and easier to interact with than Xlib. So I recommend that you move directly to XCB.  Create a new, fresh, state of art toolkit on XCB with [Cairo graphics...]("http://cairographics.org")   ([samples...]("http://cairographics.org/samples/"))

See: [http://en.wikipedia.org/wiki/XCB](http://en.wikipedia.org/wiki/XCB) and [http://xcb.freedesktop.org/](http://xcb.freedesktop.org/)

Whatever you choose so make sure you stick to Freedesktop.org's spesifications. 
[http://www.freedesktop.org/wiki/Specifications?action=show&redirect=Standards](http://www.freedesktop.org/wiki/Specifications?action=show&redirect=Standards)
Most toolkits already comply to them.

Important resources: [http://www.futuredesktop.org/opportunities.html](http://www.futuredesktop.org/opportunities.html)

I quess: GTK and QT developers will most likely move to XCB within this year and the first XCB based window manager will also emerge.

---

### Post by hype on 2007-08-10
Thanks moma, really interesting.
I read that ubuntu has used xcb , but removed it for feisty because it broke Java.
Are there any other know issues?
Is it actually possible to compile X11 with xcb support on ubuntu feisty or gutsy?
I think it's something for gutsty +1 but i'm rather curious. :)

---

