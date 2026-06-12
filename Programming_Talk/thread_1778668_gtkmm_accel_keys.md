---
title: "gtkmm accel keys"
date: 2011-06-09
forum: Programming Talk
---

### Post by tbastian on 2011-06-09
I'm building a gtkmm application, and I'm having difficulties with accel keys. How to I get the 'F' keys to be shortcuts for stuff (eg. F1 for help, F11 for fullscreen)? When adding menu items, if I use Gtk::Stock::OPEN, and then set up the accel group from the UI manager, it works fine, but I can't find a way to connect an accel key to an existing accel group.

---

### Post by simeon87 on 2011-06-09
In Python it works like this:

```
key, mod = gtk.accelerator_parse(accelerator)
item.add_accelerator("activate", accel_group, key, mod, gtk.ACCEL_VISIBLE)
```

where accelerator is something like "<Ctrl>N" and accel_group has been created like ```
accel_group = gtk.AccelGroup()
self.add_accel_group(accel_group)
```

where self is a gtk.Window. I just checked and you can also have "F1" as accelerator for the F1 key. Now it's up to you to do something similar in gtkmm.

---

### Post by tbastian on 2011-06-09
Got it. Through what you were saying I found the examples in the gtkmm package. This is how I did it. (I created my menu from an xml string)

```
act_group -> add ( Gtk::Action::create ( "Fullscreen", Gtk::Stock::FULLSCREEN ),
		Gtk::AccelKey("F11"),
		sigc::mem_fun ( *this, &MainWindow::on_view_fullscreen ));
```
and...
```
add_accel_group ( ref_UIManager -> get_accel_group ());
```
Where "Fullscreen" corresponds to a menu item in my xml string.

---

