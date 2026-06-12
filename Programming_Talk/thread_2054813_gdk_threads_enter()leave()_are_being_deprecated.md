---
title: "gdk_threads_enter()/leave() are being deprecated"
date: 2012-09-08
forum: Programming Talk
---

### Post by bird1500 on 2012-09-08
Hi,
As of Gtk 3.6 these methods are deprecated.
Is there any official documentation on this and what's the official new rules to do threading with the Gtk 3.6+ versions?

So far I only found [devs]("https://mail.gnome.org/archives/gtk-devel-list/2012-August/msg00040.html") [arguing]("https://mail.gnome.org/archives/gtk-devel-list/2012-August/msg00021.html") about it.

---

### Post by SledgeHammer_999 on 2012-09-08
You can always inform the GUI thread to update by using idle timers or asycronous queues. (both are in glib)

---

### Post by bird1500 on 2012-09-09
Thanks, I know in programming there's always a few ways to do the same thing, that's not really what I'm asking.

I'm just curious about a clear explanation where they're heading to, what's the upcoming threading model and why those decisions. gdk_threads_enter/leave work just fine, and are better in the sense that my source code is less fragmented e.g. doesn't have to be scattered across extra methods.

So I wonder are they just trying to force programmers to use only one threading approach or are there serious technical difficulties supporting gdk_threads_enter/leave, or maybe something else.

---

