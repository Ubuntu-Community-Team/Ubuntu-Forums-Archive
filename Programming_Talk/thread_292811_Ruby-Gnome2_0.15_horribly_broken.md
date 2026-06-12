---
title: "Ruby-Gnome2 0.15 horribly broken?"
date: 2006-11-04
forum: Programming Talk
---

### Post by lutzky on 2006-11-04
Applications that worked perfectly fine in ruby-gnome2-0.14 now constantly generate warnings such as

```
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
./antigibberish: line 4
   GLib-GObject-WARNING **:IA__g_object_notify: object class `GtkTextBuffer' has no property named `copy-target-list'
./antigibberish: line 4
   GLib-GObject-WARNING **:IA__g_object_notify: object class `GtkTextBuffer' has no property named `copy-target-list'

```

Sometimes they segfault, sometimes they get broken pointers and glib forces a quit. Glade is broken (the fix is easy, see [https://launchpad.net/distros/ubuntu/edgy/+source/ruby-gnome2/+bug/66623](https://launchpad.net/distros/ubuntu/edgy/+source/ruby-gnome2/+bug/66623))

The question is - why do we bother? It's a broken release altogether, it seems... why did it get into edgy? I mean, cutting-edge and all, I know, but there's a limit.

How can one install ruby-gnome2-0.14 easily in Edgy?

---

