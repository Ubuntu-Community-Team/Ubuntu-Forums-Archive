---
title: "Trying to use GTK / Glade, but having problem with documentation"
date: 2006-11-03
forum: Programming Talk
---

### Post by Daveski on 2006-11-03
Hi there.

I am playing with creating my first simple GUI app but having trouble finding documentation and examples that I can understand.

I have Glade installed and this seems quite easy to use, but I am trying to find out how to get and set Widget properties in plain old c. For example I have found:

```
 gtk_label_set_text(GTK_LABEL(label), "Some Text");
```

To set the text property of a Label Widget, but I really cannot find this documented anywhere - I have ruined my eyes browsing through the GTK+ API Docs. How for example can I get the 'Active' property of say a CheckButton or a ToggleButton?

If anyone can point me in the direction that I have obviously missed, I would be most grateful.

---

### Post by loell on 2006-11-03
[http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#gtk-label-set-text]("http://developer.gnome.org/doc/API/2.0/gtk/GtkLabel.html#gtk-label-set-text")

have you been here already?

---

### Post by Daveski on 2006-11-03
Ah, I have been here, but I see the function now. Does this mean for finding  the Active property of the buttons I need to use this:

```
g_object_get () 
```

---

### Post by Daveski on 2006-11-05
This does seem to work, so within a checkbutton toggle event I am doing this:

```
GtkWidget * check = lookup_widget(GTK_WIDGET(togglebutton), "checkbutton01");

gboolean b_act;
g_object_get(GTK_BUTTON(check), "active", &b_act, NULL);
```

and I can check the value of b_act to see if the checkbutton 'active' property is TRUE or FALSE. Is this the correct approach, as this seems a bit of a round about way, especially since it is the widget's own event.

Can anyone give me a more elegant method?

Thanks.

---

### Post by loell on 2006-11-05
imho, the code does fine

---

