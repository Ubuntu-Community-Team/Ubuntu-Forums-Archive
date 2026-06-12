---
title: "Libglade and passing user_data"
date: 2007-04-30
forum: Programming Talk
---

### Post by Laterix on 2007-04-30
I have created a .glade file with glade-3, but I'm confused how to pass user_data. Ok let's see some code first:

```

int
main (int argc, char *argv[])
{
  GladeXML *xml;
  xml = glade_xml_new (PACKAGE_SOURCE_DIR "/Livingroom.glade", NULL, NULL);
  glade_xml_signal_autoconnect (xml);

```
So, I want to use autoconnect and determine user_data with glade-editor. I want to pass this xml-pointer so that I can get widget pointers in callback functions.

In glade file it looks like this
```

<signal name="activate" handler="show_preferences_window" object="xml"/>

```

And callbacks are like this
```

void
show_preferences_window (GtkWidget * widget, gpointer user_data)
{
  GladeXML *xml = GLADE_XML(user_data);
  GtkWidget *pref_window = glade_xml_get_widget (xml, "preferences_window");
  gtk_widget_show (pref_window);
}

```

And runtime error on callbacks first line is
```

GLib-GObject-WARNING **: invalid cast from `GtkToolButton' to `GladeXML'

```

So it seems that it gives an event source object as a user_data instead of GlideXML which I wanted. Is this a bug in libglade or am I missing something here?

---

### Post by Laterix on 2007-05-01
Anyone...? Pretty please :)

---

### Post by PointSource on 2007-05-01
I had/have a similar problem, but mine was/is to do with passing data through the glade GUI.

---

