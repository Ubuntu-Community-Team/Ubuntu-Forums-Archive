---
title: "GtkWidget &quot;property&quot;"
date: 2009-12-25
forum: Programming Talk
---

### Post by Milliways on 2009-12-25
How does one get the "has_focus" property?

---

### Post by OgreProgrammer on 2009-12-25
Click on it I believe.

---

### Post by nvteighen on 2009-12-25
What do you mean? Getting the "has_focus" status? Use **gtk_widget_has_focus(GtkWidget *)** (this is in the original GTK+ C library).

---

### Post by Milliways on 2009-12-25
> **nvteighen said:**
> What do you mean? Getting the "has_focus" status? Use **gtk_widget_has_focus(GtkWidget *)** (this is in the original GTK+ C library).

I found this macro definition:-

#define GTK_WIDGET_HAS_FOCUS(wid)	  ((GTK_WIDGET_FLAGS (wid) & GTK_HAS_FOCUS) != 0)

The GtkWidget lists a number of Properties, one of which is the "has-focus" property, but does not seem to explain how to use these properties.

  "has-focus"                gboolean              : Read / Write
Whether the widget has the input focus.


It is possible that the GTK_WIDGET_HAS_FOCUS macro is the implementation, but what about the "name" property

  "name"                     gchar*                : Read / Write
The name of the widget.

---

### Post by napsy on 2009-12-26
Or you could use
```

g_object_get_property ()

```

To get the property you want but it's easier to use the convenience function already mentioned (eg. GTK_WIDGET_HAS_FOCUS()).

---

### Post by nvteighen on 2009-12-26
> **Milliways said:**
> I found this macro definition:-

#define GTK_WIDGET_HAS_FOCUS(wid)	  ((GTK_WIDGET_FLAGS (wid) & GTK_HAS_FOCUS) != 0)

The GtkWidget lists a number of Properties, one of which is the "has-focus" property, but does not seem to explain how to use these properties.

  "has-focus"                gboolean              : Read / Write
Whether the widget has the input focus.


It is possible that the GTK_WIDGET_HAS_FOCUS macro is the implementation, but what about the "name" property

  "name"                     gchar*                : Read / Write
The name of the widget.

No, I mean the gtk_widget_has_focus() function, not the macro definition. [http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-has-focus](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-has-focus)

---

### Post by Milliways on 2009-12-26
> **nvteighen said:**
> No, I mean the gtk_widget_has_focus() function, not the macro definition. [http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-has-focus](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-has-focus)

This says "Since 2.18" I am using GTK+ 2.16.1 (download for Ubuntu 9.04)

Thanks for the responses.

---

