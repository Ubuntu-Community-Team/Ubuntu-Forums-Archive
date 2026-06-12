---
title: "PyGTK process events"
date: 2008-01-16
forum: Programming Talk
---

### Post by jtourville on 2008-01-16
Hi, I'm looking for a function in PyGTK that will cause GTK to process any pending events.

I've got a simple window with a button and text view, and clicking the button triggers a long running function that periodically places status information in the text view.  Of course, the window will lock up and never update the text view until returning from that button handler.

Basically, I'm looking for the PyGTK equivalent to Qt's QApplication :: processEvents().  I just want to be able to call this function in my button's click handler to periodically allow the window to repaint and show my status updates.  I'm sure GTK has this ability, but my googling has come up empty.  I'd appreciate any help!

---

### Post by Wybiral on 2008-01-16
I think "queue_draw" might be what you're looking for.

---

### Post by jtourville on 2008-01-16
> **Wybiral said:**
> I think "queue_draw" might be what you're looking for.

Thanks for the speedy response.  queue_draw didn't do the trick, but in the documentation I did find something that looks promising: gtk.gdk.window_process_all_updates().  The documentation suggests it will do what I want, but it references gtk.gdk.Window, and I'm using gtk.Window.

From the documentation, gtk.gdk.Window looks like a low level type not intended to be used for a simple top level window.  Guess I'll have to do some digging on that, I'm hoping I won't have to manually construct a low level window just over this little issue.  :)

---

### Post by Quikee on 2008-01-16
> **jtourville said:**
> Thanks for the speedy response.  queue_draw didn't do the trick, but in the documentation I did find something that looks promising: gtk.gdk.window_process_all_updates().  The documentation suggests it will do what I want, but it references gtk.gdk.Window, and I'm using gtk.Window.

From the documentation, gtk.gdk.Window looks like a low level type not intended to be used for a simple top level window.  Guess I'll have to do some digging on that, I'm hoping I won't have to manually construct a low level window just over this little issue.  :)

Just access the gtk.gdk.Window with "widget.window" - some widgets have it (like for example gtk.Window, gtk.Button, ...) some don't, and those who do have it only get it when they are realized.

---

### Post by llonesmiz on 2008-01-17
I think [this]("http://faq.pygtk.org/index.py?req=show&file=faq03.007.htp") can help you.

---

### Post by jtourville on 2008-01-17
> **llonesmiz said:**
> I think [this]("http://faq.pygtk.org/index.py?req=show&file=faq03.007.htp") can help you.

```
 while gtk.events_pending():
    gtk.main_iteration(False)
```

Thanks, that's exactly what I needed!  :)

---

### Post by asmoore82 on 2010-12-01
> **llonesmiz said:**
> I think [this]("http://faq.pygtk.org/index.py?req=show&file=faq03.007.htp") can help you.
[SIZE="3"]Thanks++[/SIZE]

Much wide open googling for a python programming problem -
and the best answer is finally found @ubuntuforums :KS

---

