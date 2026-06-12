---
title: "[Gtk] How to remove and add back a widget to container?"
date: 2012-01-18
forum: Programming Talk
---

### Post by t1497f35 on 2012-01-18
Hi,
I remove a previously added widget to a Gtk::HBox this way:
remove(*widget);
delete widget;
widget = NULL;

then add one back:
widget = new Gtk::Button(...);
pack_start(*widget, false, false);

but nothing happens, the new widget doesn't appear. Any ideas?

---

### Post by CoffeeRain on 2012-01-18
Did you mean to mark this as solved?

---

