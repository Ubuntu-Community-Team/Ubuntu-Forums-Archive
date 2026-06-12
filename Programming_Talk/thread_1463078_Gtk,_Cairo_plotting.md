---
title: "Gtk, Cairo plotting"
date: 2010-04-26
forum: Programming Talk
---

### Post by tbastian on 2010-04-26
I'm currently making a small plotting library for use in a real time plotting application. I tried GTK plot, but the documentation was terribly outdated, and gtkdatabox was too slow, so I got the beginnings of a plotting library a colleague of mine had written and I'm refactoring it and adding some stuff. Eventually I'd like to make it into a strip chart.

Anyway, my issue is this: When I try to plot something and just leave it, it works just fine. When I try to update it (at anywhere from 1-32 hz), the program crashes with any number of errors. Here are the most common.

```
testplot: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

The program 'testplot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 1253 error_code 1 request_code 0 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Does anybody have any clues as to how I should fix it?

I have attached a small test program if anyone would like to play around with it...

---

### Post by mmix on 2010-04-26
see gtkplot in gtk+extra-2.1.2.tar.gz
[http://gtkextra.sourceforge.net/](http://gtkextra.sourceforge.net/)

---

### Post by kknd on 2010-04-26
This kind of error is usually related with multiple threads using GTK+. I don't know how you are managing the threads that you've created, but try to delegate all tasks that uses GTK+ to the main (initial) thread.

---

### Post by tbastian on 2010-04-27
> **kknd said:**
> This kind of error is usually related with multiple threads using GTK+. I don't know how you are managing the threads that you've created, but try to delegate all tasks that uses GTK+ to the main (initial) thread.

I added```
gtk_timeout_add( 500, redraw, NULL)
``` and that seemed to fix it! Thanks so much, it was driving me insane!

---

### Post by kknd on 2010-04-27
You're welcome. gtk_timeout_add is deprecated (will be removed in GTK 3+, try to change it to g_timeout_add).

---

### Post by tbastian on 2010-04-27
> **kknd said:**
> You're welcome. gtk_timeout_add is deprecated (will be removed in GTK 3+, try to change it to g_timeout_add).

Ok, I did that. Thanks for the heads up.

---

