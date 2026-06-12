---
title: "pyGTK/Glade catch righ-click event on a button"
date: 2009-10-11
forum: Programming Talk
---

### Post by J V on 2009-10-11
I'm trying to determine weather it was a right-click or a left-click issued to my button, but all the FAQs etc presume an "Event" parameter, which is nowhere to be found on my button...

Anyone ever done this before?

---

### Post by diesch on 2009-10-11
You define a event handler like that

```

def on_button_press_event(self, widget, event):
  if event.type == gtk.gdk.BUTTON_PRESS and event.button == 3:
     print "It's a right click!"

```and connect it with button-press-event:

```

your_button.connect('button-press-event', self.on_button_press_event)

```

---

### Post by J V on 2009-10-11
Well here are my problems, firstly, its loading from glade (So no tampering with code #2), secondly, if I try code number one...

```
TypeError: on_stats_load_clicked() takes exactly 3 arguments (2 given)
```

---

### Post by diesch on 2009-10-11
You have to connect it with "button-press-event", not "clicked". So it should be called "on_stats_load_button_press_event".

---

### Post by J V on 2009-10-11
I presume thats pressed under gtkButton in glade? If not, I don't know what you're talking about.

Edit: Ok, I see what you mean, is there an autoconnect(self) for events?

---

### Post by diesch on 2009-10-11
> **J V said:**
> I presume thats pressed under gtkButton in glade? If not, I don't know what you're talking about.


In Glade it's in the Button's signals properties under gtkWidget

> **J V said:**
> 
Edit: Ok, I see what you mean, is there an autoconnect(self) for events?


gtk.Builder has [connect_signals]("http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html#method-gtkbuilder--connect-signals") and gtk.glade.XML [signal_autoconnect]("http://library.gnome.org/devel/pygtk/stable/class-gladexml.html#method-gladexml--signal-autoconnect")

---

### Post by J V on 2009-10-11
ahh, so it is under signals, thanks for the help, that works now :)

---

