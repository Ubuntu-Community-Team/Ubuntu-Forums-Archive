---
title: "Gtkmm cross compile"
date: 2010-12-12
forum: Programming Talk
---

### Post by roadkillguy on 2010-12-12
Has anyone been able to get gtkmm (c++ gtk) cross compiling to windows? They only seem to give out an installer to install gtkmm-devel or whatever onto the system, which is an exe, and alas I cannot use it.  After much googling, that seems to be the only way to install gtkmm.

P.S. I'm using c++ and mingw.

All help is much appreciated.  Thanks!

---

### Post by roadkillguy on 2010-12-20
I solved it myself.  It took me a while, but I have it working.  I simply copied all of the installed include directory to /usr/i586-mingw32msvc/include/ .  I then renamed all *.dll.a libs to *.a and placed them in lib too.  After converting the pkg-config output to /usr/i586-mingw32msvc/ instead of just /usr/, it seemed to build ok with some minor fixes.  (Some libraries weren't necessarily named .dll.a so I had to copy them over too)

ANYWAY :D

The result is that gtkmm doesn't really look like a native windows application.  It has the same layout as ubuntu, which is nice, but it's completely boxy and has no color whatsoever.  How do I make it look like windows?  If I can't, how do I make it at least have SOME color?  It's kind of bland.

Should I switch to something else?  QT?  WxWidgets?  Google images isn't the best resource for how these gui's look under windows.

---

### Post by nvteighen on 2010-12-20
> **roadkillguy said:**
> 
Should I switch to something else?  QT?  WxWidgets?  Google images isn't the best resource for how these gui's look under windows.

WxWidgets will default to the native GUI toolkit, so if that's important for you, it's what you want. Qt looks great in Windows, but non-native... And GTK+, well, the problem is that in GNOME we cover the faulty default look by using gtk2-engine themes... but try running a GTK+ app in KDE or GNUStep and it will look almost as it does in Windows.

---

### Post by roadkillguy on 2010-12-20
> **nvteighen said:**
> WxWidgets will default to the native GUI toolkit, so if that's important for you, it's what you want. Qt looks great in Windows, but non-native... And GTK+, well, the problem is that in GNOME we cover the faulty default look by using gtk2-engine themes... but try running a GTK+ app in KDE or GNUStep and it will look almost as it does in Windows.

So essentially gtk has a default look that only linux changes? I think I'll have to look into wxWidgets.  Thanks!

Also, does wxWidgets require you to include 15+ dll's with your binary?  If it defaults to the native GUI, it shouldn't right?

---

### Post by nvteighen on 2010-12-20
> **roadkillguy said:**
> So essentially gtk has a default look that only linux changes?

No, GNOME is able to change it because it takes full advantage of GTK+. Install the KDE Desktop Environment on your computer and try running Gedit from there.

> 
Also, does wxWidgets require you to include 15+ dll's with your binary?  If it defaults to the native GUI, it shouldn't right?

Honestly, I never touched wxWidgets, but I guess the number of shared libraries it uses should be significantly smaller than any other GUI toolkit because of this.

---

