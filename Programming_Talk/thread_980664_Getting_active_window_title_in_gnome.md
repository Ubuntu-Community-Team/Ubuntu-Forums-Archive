---
title: "Getting active window title in gnome"
date: 2008-11-13
forum: Programming Talk
---

### Post by lviggiani on 2008-11-13
Hi guys,
I'm trying to get current active window title in a vala applicaction (but any other language is welcome).

With...
```
Gdk.Screen.get_default().get_active_window()
```
... I have a Gdk.Window object actually pointing to screen active top level window but unfortunately there is no method to get its title.
The funny thing to me is that I can SET its title...
```
Gdk.Screen.get_default().get_active_window().set_title("Foo");
```

I see that Gtk (not Gdk) Window class has a method to get title but I don't know how to get a Gtk.Window from a Gdk.Window (and if it is the right way).

Can anyone help me please?
Thanks in advance

---

