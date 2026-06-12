---
title: "Configure Xterm for mouse events with Ncurses."
date: 2009-11-22
forum: Programming Talk
---

### Post by Renée Jade on 2009-11-22
Hey guys,

I've been working on a simple C program that uses the ncurses library and I can't seem to get it to work with mouse events. The only events I'm interested in are clicks. When I click, a character is read by getch(), but it is not being read as a KEY_MOUSE. I have a feeling that the problem is with my Xterm configuration and not with my code. Does anyone know what might be causing this behavior or how to fix it?

Thanks heaps,


Renée.

---

### Post by asashnov on 2009-11-27
rmev from gpm package can read mouse events under xterm

---

### Post by itcotbtoemik on 2009-11-27
There's no sample code shown. The most likely reason for not getting
the KEY_MOUSE would be having not called keypad() to enable that.
Other reasons might include incorrect $TERM setting (since ncurses
uses that information).

Running gpm in xterm doesn't serve much useful purpose unless you
like to generate bug reports.

---

