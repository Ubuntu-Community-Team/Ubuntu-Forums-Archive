---
title: "What do the Gtk-WARNING messages mean"
date: 2010-01-20
forum: Programming Talk
---

### Post by Milliways on 2010-01-20
Does anyone know of a link to explain the meaning of the gtk+ error messages?

e.g
(gtree:5804): Gtk-WARNING **: Unknown property: GtkVPaned.orientation

what does the 5804 mean?

This message is one of the clearer messages, but how does one locate the offending widget?

---

### Post by saulgoode on 2010-01-20
It's not a direct answer to your question, but a really cool tool for introspection of GTK widgets is [GTK Parasite]("http://chipx86.github.com/gtkparasite/").

---

### Post by denarced on 2010-01-21
> **Milliways said:**
> Does anyone know of a link to explain the meaning of the gtk+ error messages?

e.g
(gtree:5804): Gtk-WARNING **: Unknown property: GtkVPaned.orientation

what does the 5804 mean?

This message is one of the clearer messages, but how does one locate the offending widget?

I think it means GtkVPaned doesn't have a property with the name 'orientation', which I think it doesn't have

---

