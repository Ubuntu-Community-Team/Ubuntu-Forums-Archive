---
title: "Adding a widget to a toolbar GTK+"
date: 2011-08-24
forum: Programming Talk
---

### Post by nickos on 2011-08-24
How can  i add a widget to a toolbar?
Rather than creating tool items.

For ex, i succesfully added  a tool_button_new_from_stock but i cant add a combobox! :confused:

---

### Post by nickos on 2011-08-24
help!

---

### Post by nickos on 2011-08-24
Solved.I found a proper solution myself.

I made a new toolbar item and since its GtkBin i added the widget to it as  a child and added the new toolbar item to the toolbar.

---

