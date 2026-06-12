---
title: "How to open the default web browser from within a C program"
date: 2008-12-04
forum: Programming Talk
---

### Post by tananaBrian on 2008-12-04
Hi,

  We're writing cross-platform applications in C, via GTK+, that have help systems associated with them.  Currently, the Linux side of the fence opens a GTK+ window and populates it with help text (no links!) while the Windoze side uses Microshaft's compiled help system.  What we'd *like* to do is to switch to HTML help across the board, display the help by programmatically opening a web browser, and use the HTML editor of our choice on either platform.  I know how to open the default web browser under Windoze, but ...in Linux?  Help!  On this one I'm clueless and not having a lot of luck in web searches on the topic.  Again, here are the goals:

=> Know how to determine the 'default' (if such a concept exists) browser and path on a Linux box ...from within a running C program, and then to run it with to open an HTML file (our help system.)

Thanks,
Brian

---

### Post by mssever on 2008-12-04
> **tananaBrian said:**
> Hi,

  We're writing cross-platform applications in C, via GTK+, that have help systems associated with them.  Currently, the Linux side of the fence opens a GTK+ window and populates it with help text (no links!) while the Windoze side uses Microshaft's compiled help system.  What we'd *like* to do is to switch to HTML help across the board, display the help by programmatically opening a web browser, and use the HTML editor of our choice on either platform.  I know how to open the default web browser under Windoze, but ...in Linux?  Help!  On this one I'm clueless and not having a lot of luck in web searches on the topic.  Again, here are the goals:

=> Know how to determine the 'default' (if such a concept exists) browser and path on a Linux box ...from within a running C program, and then to run it with to open an HTML file (our help system.)

Thanks,
Brian
For Gnome, you can read the gconf key /desktop/gnome/applications/browser/exec. I don't know about KDE.

Oh, also, check out xdg-open. It's probably better than messing with gconf, but I have no direct experience with it.

---

### Post by kknd on 2008-12-04
gtk_show_uri (), in gtk >= 2.14

---

### Post by cszikszoy on 2008-12-04
What you want is xdg-open.  Open up a terminal and try it for yourself

```

xdg-open http://www.google.com

```Check out more info on xdg-utils here: [http://portland.freedesktop.org/wiki/](http://portland.freedesktop.org/wiki/)

---

### Post by Vadi on 2008-12-04
I second xdg-open. It's a desktop-neutral way to opening things, installed in Ubuntu by default.

---

### Post by SimonJohnes on 2008-12-05
The information you have given kknd, is it be useful because i couldn't find any solution through out the search except on ubuntu forum.

---

