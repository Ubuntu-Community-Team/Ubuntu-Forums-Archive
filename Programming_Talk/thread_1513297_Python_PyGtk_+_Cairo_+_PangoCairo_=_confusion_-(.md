---
title: "Python: PyGtk + Cairo + PangoCairo = confusion :-("
date: 2010-06-19
forum: Programming Talk
---

### Post by JLTB on 2010-06-19
Hello, as a hobby I'm writing a few GTK application using Python.  Recently I've been trying out Cairo and PangoCairo.

My problem is I am often getting errors like this, and I don't know what is causing them or where I should start debugging.
```

The program 'testcairopango2.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 212 error_code 9 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Here are two scripts, nearly identical.  The first one (testcairopango.py) is not interactive and works fine.  The second (testcairopango2.py) uses a "keypress" event to draw text on the screen.  

The second script crashes as soon as you press a key, why?

PS: If you can recommend any Python OSS projects using Cairo + PangoCairo, preferably with clean readable code, that would be an added bonus!

Thanks!

James

---

### Post by simeon87 on 2010-06-19
The problem is probably that the window of the widget gets invalidated from time to time. The interactive code works when I add

```
self.widget = widget
```

to the beginning of expose and the following to the beginning of textPaint:

```
self.context = self.widget.window.cairo_create()
self.pangocontext = pangocairo.CairoContext(self.context)
```

In other words, I'm recreating the contexts again. I would redesign the software in such a way that this is not necessary. For example, by having one expose event that handles everything. Depending on the type of application, this does not need to be inefficient. If it does turn out to be inefficient, you can optimize it then.

---

### Post by JLTB on 2010-06-19
Great, I will give this a try simeon87.  Thanks!

To make sure I understand the concept, you are recommending I essentially redraw the entire screen each time it needs updating?

---

### Post by simeon87 on 2010-06-19
Yes, you would handle all rendering through the expose event. This is the simplest design that I know and simple is usually the best. That doesn't mean you have to repaint everything though as you could use some flags to keep track of what needs to be rendered and what not. In addition, you could look into the area value of the expose event (event.area) which specifies the area that needs to be repainted (see [docs](http://developer.gnome.org/doc/GGAD/sec-gdkevent.html)). You can also specify this yourself when requesting a repaint: [queue_draw_area](http://www.pygtk.org/docs/pygtk/class-gtkwidget.html#method-gtkwidget--queue-draw-area).

---

### Post by JLTB on 2010-06-19
Very helpful, thank you.

---

