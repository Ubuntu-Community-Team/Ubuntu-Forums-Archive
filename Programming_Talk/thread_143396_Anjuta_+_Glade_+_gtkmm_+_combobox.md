---
title: "Anjuta + Glade + gtkmm + combobox"
date: 2006-03-12
forum: Programming Talk
---

### Post by qferret on 2006-03-12
If I use gtkmm 2.4 when creating a GUI, comboboxes work (at least they show up)

If I use gtkmm 2.0, comboboxes error out on build:

```

/usr/include/gtkmm-2.0/gtkmm/celllayout.h:156: error: ‘sigc’ has not been declared
/usr/include/gtkmm-2.0/gtkmm/celllayout.h:156: error: ISO C++ forbids declaration of ‘slot’ with no type
/usr/include/gtkmm-2.0/gtkmm/celllayout.h:156: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/celllayout.h:158: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/celllayout.h:158: error: ISO C++ forbids declaration of ‘SlotCellData’ with no type
/usr/include/gtkmm-2.0/gtkmm/combobox.h:290: error: ‘SlotRowSeparator’ in class ‘Gtk::TreeView’ does not name a type
/usr/include/gtkmm-2.0/gtkmm/combobox.h:297: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/combobox.h:297: error: ISO C++ forbids declaration of ‘SlotRowSeparator’ with no type

```

Is there a way to get Anjuta to use 2.4 when building? If I have 2.4 installed, Anjuta still looks for 2.0 & fails. Is there a symlink I can change somewhere to make it look at the other? (like you can make gcc point to either gcc-3.4 or gcc-4.0)

---

### Post by qferret on 2006-03-13
damn.... nobody else has run across this?

That kinda bites. Glade looked like a cool tool, especially since you can open it directly from within Anjuta, but if I can't even use a combobox.....???

---

### Post by MicahCarrick on 2006-03-16
There *is* a way to get anjuta to use the other library, I just can't recall how. Whenever I can't get Anjuta to do what I want I just go in and hack the configure.in and/or makefile.am files myself.  Have you asked on the gtkmm or anjuta-users mailing list?

---

