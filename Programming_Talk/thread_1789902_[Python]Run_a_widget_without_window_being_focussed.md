---
title: "[Python]Run a widget without window being focussed"
date: 2011-06-24
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-24
hi all i hav written a code in pygtk that captures the keys that a user presses while the widget is running..but only when it is in focus...so is thre anything which can make it run without it in focus....???
the code is
```

import pygtk,gtk
def on_key_press_event(widget, event):
    keyname = gtk.gdk.keyval_name(event.keyval)
    print "Key %s (%d) was pressed" % (keyname, event.keyval)

w = gtk.Window()
w.connect('key_press_event', on_key_press_event)
w.show_all()
w.connect("destroy",lambda wid:gtk.main_quit())
gtk.main()

```

---

### Post by nvteighen on 2011-06-24
> **Dhiraj Thakur(Invincible) said:**
> hi all i hav written a code in pygtk that captures the keys that a user presses while the widget is running..but only when it is in focus...so is thre anything which can make it run without it in focus....???
the code is
```

import pygtk,gtk
def on_key_press_event(widget, event):
    keyname = gtk.gdk.keyval_name(event.keyval)
    print "Key %s (%d) was pressed" % (keyname, event.keyval)

w = gtk.Window()
w.connect('key_press_event', on_key_press_event)
w.show_all()
w.connect("destroy",lambda wid:gtk.main_quit())
gtk.main()

```

Not with GTK+. Think about this: that gtk.main() is running in the context of your program, so it will catch the signals that your program gets... nothing else.

You have to interface with the X server, which is the system component in charge of detecting keypresses in a graphical display session. Look at this: [http://www.larsen-b.com/Article/184.html](http://www.larsen-b.com/Article/184.html)

---

