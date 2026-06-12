---
title: "How to change Gtk::Label font?"
date: 2005-12-03
forum: Programming Talk
---

### Post by mdurham on 2005-12-03
Hi each,
I'm using gtkmm (well, trying to!)
Any advice on how to change the font type & size and bg colour of a Gtk::Label or/and Gtk::Entry?
I can't find an example anywhere.

TIA Mike

---

### Post by nagilum on 2005-12-04
Though I don't have an example for gtkmm here's one in plain C. The font of any GtkWidget can be modified like this.

```


GtkWidget *label;

label = gtk_label_new ("hello world");
gtk_widget_modify_font (label,
  pango_font_description_from_string ("Monospace 10")
);

```

---

### Post by Roptaty on 2005-12-04
You can also use Pangos markup language
```

Gtk::Label lab;
lab.set_markup("<span background=\"black\" foreground=\"red\">Gin and Tonic</span>");

```

---

### Post by mdurham on 2005-12-04
Thanks guys that's a great help.
Mike

---

