---
title: "Adding text to a combobox"
date: 2007-10-18
forum: Programming Talk
---

### Post by marcos.linux on 2007-10-18
I'm having a tough time trying to figure out the problem here:

I made a window under Glade in wich has 1 entry box, 1 combobox and 1 button, the button adds the text from entry1 to combobox1. But when I click the button, I get this:

self.window.get_widget("combobox1")insert_text(0, str(self.window.get_widget("entry1").get_text())

GtkWarning: gtk_combo_box_insert_text: assertion `GTK_IS_LIST_STORE (combo_box->priv->model)' failed


What am I doing wrong?

---

