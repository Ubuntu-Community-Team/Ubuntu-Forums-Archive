---
title: "Using a tree model with a combo box in GTK"
date: 2009-05-29
forum: Programming Talk
---

### Post by Origin415 on 2009-05-29
Hello,

I'm trying to set up a simple program in glade/gtk, and I wanted to have drop down lists with grouped options. Using GTK, this is possible, but as you can see in the attachment, it isn't quite what I what I was looking for: I only want the Scans to be selectable, not the Groups. Is it possible to somehow get rid of those options, or is there a similar widget I should look at to get what I want?

Thanks

---

### Post by crdlb on 2009-05-29
I'm not sure how you've done that, but a plain GtkComboBox does not have submenu titles like that. As far as I know, that could only be done by explicitly adding those elements and setting a row separator func to get the separator.

---

### Post by Origin415 on 2009-05-29
You can create a tree model and add it to the combo box with gtk_combo_box_set_model

---

### Post by crdlb on 2009-05-29
I know about submenus in a ComboBox, but I've never seen it automatically add headers like that. I meant to point you to the "Combo boxes" example in gtk-demo. The second combobox in that example works like you want, I think.

---

### Post by Origin415 on 2009-06-01
It does do it by default, but the demo had some cell rendering magic to make them go away. Thanks for the help, its exactly what I wanted now :D

---

