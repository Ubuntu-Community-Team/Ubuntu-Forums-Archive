---
title: "Pango Blues"
date: 2006-05-29
forum: Programming Talk
---

### Post by Raoul Duke on 2006-05-29
So I am writing my first program for Linux/GTK and everything is going fine, until I run into Pango. Seems that one must be at least 1/2 Vulcan to draw text on the display. So I wonder if there exists some front-end functions to Pango for use by human beings? If not, I will have to code some myself, but the results will no doubt be less than ideal, as I lack the necessary green corpuscles.

Anyone have such a thing?

---

### Post by Raoul Duke on 2006-05-29
Nobody?
So how do you all do text in a (resizeable) GTK window? Maybe be some way I don't know about?

---

### Post by psychicdragon on 2006-05-30
Um, what language are you writing your program in? Did you look at the docs at all? You just want to display some text, formatted using Pango markup, right?

Presuming you're using C:
```
my_label = gtk_label_new (NULL);
gtk_label_set_markup (GTK_LABEL (my_label), "<b><big>WOW! Big Text!!!one111!</big></b>");
```

[GTK+ Reference Manual]("http://developer.gnome.org/doc/API/2.0/gtk/index.html"): Read it.

---

