---
title: "Warning when running Gtk code.. spurious??"
date: 2009-12-05
forum: Programming Talk
---

### Post by bcz on 2009-12-05
I get a runtime warning..

 "Glib-GObject-WARNING **: invalid cast from 'GtkTextBuffer' to GtkObject'

when running following code

view=gtk_text_view_new();
buffer=gtk_text_view_get_buffer(GTK_TEXT_VIEW(view));
g_signal_connect(GTK_OBJECT(buffer),"changed",G_CALLBACK(changed),buffer);

the code correctly executes the callback function, but why do I get the runtime warning.  Is the warning spurious or am I overlooking an obvious error in my code

Any feedback appreciated

Rgds Bill C

---

### Post by SledgeHammer_999 on 2009-12-05
Maybe because a GtkTextBuffer isn't a GtkObject?

try this to see if the warning dissapears:
```
g_signal_connect(buffer, "changed",G_CA LLBACK(changed),buffer);
```

---

### Post by Linteg on 2009-12-05
I think it's supposed to be G_OBJECT instead of GTK_OBJECT

---

### Post by bcz on 2009-12-05
Should be G_OBJECT.   Warning disappears

Many thanks to all

Bill C

---

