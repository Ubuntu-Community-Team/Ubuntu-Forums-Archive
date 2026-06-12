---
title: "Ruby Gnome2"
date: 2006-11-02
forum: Programming Talk
---

### Post by Relain on 2006-11-02
Ola,
I've had a marvellous idea for a program which, sadly for me, requires a GUI of sorts. As such i thought i'd take the plunge and actually learn how to code a :gasp: real GUI. I grabbed the ruby-gnome2 package and started following the tutorial on the ruby-gnome/gtk site 

[http://ruby-gnome2.sourceforge.jp/hiki.cgi?tut-gtk-intro](http://ruby-gnome2.sourceforge.jp/hiki.cgi?tut-gtk-intro)

Most basic example:

```

#!/usr/bin/ruby -w
=begin
  helloworld.rb - Ruby/GTK first sample script.

  Copyright (c) 2002,2003 Ruby-GNOME2 Project Team
  This program is licenced under the same licence as Ruby-GNOME2.

  $Id: helloworld.rb,v 1.4 2003/02/01 16:46:22 mutoh Exp $
=end

require 'gtk2'

button = Gtk::Button.new("Hello World")
button.signal_connect("clicked") {
  puts "Hello World"
}

window = Gtk::Window.new
window.signal_connect("delete_event") {
  puts "delete event occurred"
  #true
  false
}

window.signal_connect("destroy") {
  puts "destroy event occurred"
  Gtk.main_quit
}

window.border_width = 10
window.add(button)
window.show_all

Gtk.main

```

which should just give a empty window spews out all this guff:

```

window.rb: line 11
   Gtk-WARNING **:Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
window.rb: line 11
   Gdk-CRITICAL **:gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
window.rb: line 11
   Pango-CRITICAL **:pango_context_set_font_description: assertion `context != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_context_set_base_dir: assertion `context != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_context_set_language: assertion `context != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_new: assertion `context != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_set_text: assertion `layout != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_set_attributes: assertion `layout != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_set_alignment: assertion `layout != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_set_width: assertion `layout != NULL' failed
window.rb: line 11
   Pango-CRITICAL **:pango_layout_get_extents: assertion `layout != NULL' failedwindow.rb: line 11
   Gtk-WARNING **:gtk_widget_size_allocate(): attempt to allocate widget with width -1386328 and height 41
window.rb: line 11
   Gdk-CRITICAL **:gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_colormap_get_visual: assertion `GDK_IS_COLORMAP (colormap)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_screen_get_default_colormap: assertion `GDK_IS_SCREEN (screen)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_enable_synchronized_configure: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_user_data: assertion `window != NULL' failed
window.rb: line 11
   Gtk-CRITICAL **:gtk_style_attach: assertion `window != NULL' failed
window.rb: line 11
   Gtk-CRITICAL **:gtk_style_set_background: assertion `GTK_IS_STYLE (style)' failed
window.rb: line 11
   Gtk-CRITICAL **:gtk_paint_flat_box: assertion `GTK_IS_STYLE (style)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_type_hint: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_accept_focus: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_focus_on_map: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_modal_hint: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gtk-CRITICAL **:gtk_window_realize_icon: assertion `widget->window != NULL' failed
window.rb: line 11
   Gtk-WARNING **:Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_resize: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_invalidate_maybe_recurse: assertion `window != NULL' failed
window.rb: line 11
   GLib-GObject-CRITICAL **:g_object_ref: assertion `G_IS_OBJECT (object)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_screen_get_root_window: assertion `GDK_IS_SCREEN (screen)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_new: assertion `GDK_IS_WINDOW (parent)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_user_data: assertion `window != NULL' failed
window.rb: line 11
   Gtk-CRITICAL **:gtk_style_attach: assertion `window != NULL' failed
window.rb: line 11
   GLib-GObject-CRITICAL **:g_object_ref: assertion `G_IS_OBJECT (object)' failed
window.rb: line 11
   Gtk-CRITICAL **:gtk_style_attach: assertion `window != NULL' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_invalidate_rect: assertion `window != NULL' failedwindow.rb: line 11
   Gdk-CRITICAL **:gdk_window_invalidate_rect: assertion `window != NULL' failedwindow.rb: line 11
   Gdk-CRITICAL **:gdk_window_unmaximize: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_unstick: assertion `GDK_IS_WINDOW (window)' failedwindow.rb: line 11
   Gdk-CRITICAL **:gdk_window_deiconify: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_unfullscreen: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_keep_above: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_set_keep_below: assertion `GDK_IS_WINDOW (window)' failed
window.rb: line 11
   Gdk-CRITICAL **:gdk_window_show: assertion `GDK_IS_WINDOW (window)' failed
window.rb:34:in `main': Interrupt

```

The clue is guess is in the 1st line: Screen for GtkWindow not set, what's that mean and how do i set it? The tutorial seems to suggest that most of the window creation magic will take care of itself. Do i need more libs or something? All the glib-dev etc libraries are up to date. Oh and i tried some of the sample programs from the ruby-gnome website and they run ok...

---

### Post by rplantz on 2006-11-02
It works for me.

Line 11 is:
```

require 'gtk2'

```
The error message suggests something related to "ruby" and "gtk2" is not installed. So I fired up synaptic an did a search on those two words. It turned up the package libgtk2-ruby. The package is installed on my system. Is it on yours?

I'm also learning this stuff, so I do not know if this is the answer. But it certainly seems like a good place to start.

---

### Post by Relain on 2006-11-03
so i tried it on my edgy laptop, i did an aptitude ruby-gnome2 install first and it appears to work. Strange because i did the same on my work machine (which is 6.06 instead). 

When it does run i get the following errors though:
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


```

I presume this is relatively usual errors for glib etc? At least this one actually draws a window and i can close it and click on the button.

---

### Post by bcbroom on 2006-11-05
You need to add this line

```
Gtk.init
```

I put it just after the require line.  From what I've read Gtk is changing so this won't be required, which may be why the line is required on Dapper and not Edgy.

---

### Post by sargate on 2006-11-18
i have the same error /usr/lib/ruby/1.8/glib2.rb: line 55
any ideas how to solve this?

---

### Post by Doovoo on 2007-02-22
I'm running edgy and getting the same error, was this ever resolved?

---

### Post by Enselic on 2007-02-24
If you download and compile Ruby-GNOME2 0.16, you should be fine.

There appears to be a bug with 0.15, which is the version the repos contains (at least last time I checked).

---

### Post by arclight on 2007-06-24
Using 'Gtk.init' solved the problem for me on Ubuntu 6.06 LTS.

---

