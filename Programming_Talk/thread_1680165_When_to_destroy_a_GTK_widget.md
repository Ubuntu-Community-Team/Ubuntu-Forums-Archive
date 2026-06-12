---
title: "When to destroy a GTK widget?"
date: 2011-02-02
forum: Programming Talk
---

### Post by ziekfiguur on 2011-02-02
Hello All,

I have recently been trying to build a GTK gui in C++, and i noticed that the documentation is not really clear about memory management.

The problem is, I am using a GTK_Notebook widget. I add the pages with
```
gtk_notebook_append_page(GTK_NOTEBOOK(d_notebook),
                             buffer->frame(),
                             buffer->label())
```
 and at some point i remove some pages from the notebook. When i called gtk_destroy_widget on the label:
```
gtk_widget_destroy(d_label)
``` (in the deconstructor of buffer)
I got this error message: ```
Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (d_label)' failed
```
So, my question is, does Gtk automatically destroy the label when I remove the page? and what about the frame?
And, more importantly, how can i know when gtk destroys a widget, and when do i have to do it myself?

---

### Post by fct on 2011-02-02
From:

[http://library.gnome.org/devel/gtk/2.99/GtkWidget.html#gtk-widget-destroy](http://library.gnome.org/devel/gtk/2.99/GtkWidget.html#gtk-widget-destroy)

> Removing a widget from its container or the list of toplevels results in the widget being finalized, unless you've added additional references to the widget with g_object_ref(). 

In most cases, only toplevel widgets (windows) require explicit destruction, because when you destroy a toplevel its children will be destroyed as well.

---

### Post by ziekfiguur on 2011-02-02
Thank you, I'm sorry I missed that in the docs.
Any idea why I could destroy the frame? (Which is a ScintillaObject btw)
Is that an accident, or is it kept alive on purpose?

---

### Post by fct on 2011-02-02
Might be unpredictable behavior or expected cause a GtkFrame is a container. Either way, IMHO it'd be better to follow the docs and only destroy top-level windows.

---

### Post by nvteighen on 2011-02-02
Uhm...

```

void gtk_notebook_remove_page(GtkNotebook *notebook, gint page_num);

```

Now, be aware that there is a GTK+ official binding for C++ called gtkmm. It integrates the GTK+ data structures into a more C++-ish programming style.

---

### Post by ziekfiguur on 2011-02-02
> **nvteighen said:**
> 
Now, be aware that there is a GTK+ official binding for C++ called gtkmm. It integrates the GTK+ data structures into a more C++-ish programming style.

Thanks for the heads-up, I'm looking into it.

---

### Post by ziekfiguur on 2011-02-06
I now have a GtkWidget created with `scintilla_new();'
Then i use `Glib::wrap()' to get a Gtk::Widget.
When the Gtk::Widget is destroyed, do i still have to clean up the GtkWidget myself?

---

