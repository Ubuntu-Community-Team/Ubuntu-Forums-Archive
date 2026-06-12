---
title: "Someone explain main loop(gstreamer related)"
date: 2008-07-24
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-07-24
Hi I am a hobbyist programmer and now I am experimenting with GTKmm and Gstreamer. I use C++ (and C for the gstreamer part). I read the docs of Gstreamer and got confused about the bus and the main loop. As I understand it, in the examples they are setting up main loops because the code-samples are console programs. But when you use a GUI toolkit(which has it's own main loop) is it wise to set up another loop too? I am referring to [this](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-bus.html#section-bus-howto)
I am totally confused. I don't know how to set it up on GTKmm. Do I need yo hook it up with GTKmm's main loop? Create another? How? Do you have any ideas?

Thank you in advance!!!

---

### Post by kknd on 2008-07-24
GTK applications run with a GMainLoop, so does Gstreamer.

When you are using both, simply use the same main loop for booth. You doesn't have to do anything, gstreamer will use the "gtk main loop" automatically.

If you want do do something more fancy, read the GLib documentation.

---

### Post by bruce89 on 2008-07-24
WARNING: I have no experience in Gtkmm, but some in GTK+.

> **kknd said:**
> When you are using both, simply use the same main loop for booth. You doesn't have to do anything, gstreamer will use the "gtk main loop" automatically.

Technically speaking, there is no "gtk main loop" any more. It is now in GLib. (strictly there is a GTK+ main loop, but it's just a compatibility layer on top of the GLib one)

[http://library.gnome.org/devel/glib/stable/glib-The-Main-Event-Loop.html](http://library.gnome.org/devel/glib/stable/glib-The-Main-Event-Loop.html) is the GMainLoop documentation.

Anyway, [http://live.gnome.org/Vala/GStreamerSample](http://live.gnome.org/Vala/GStreamerSample) would suggest you use the init functions for GTK+ and gst, then use Gtk::Main::run.

---

### Post by kknd on 2008-07-24
> **bruce89 said:**
> 

Technically speaking, there is no "gtk main loop" any more. It is now in GLib. (strictly there is a GTK+ main loop, but it's just a compatibility layer on top of the GLib one)

If you had read more carefully my post you would see that I said that the Gtk main loop is a GMainLoop (no offenses =) ).

---

### Post by SledgeHammer_999 on 2008-07-24
Thank you. I think the correct init function for GTKmm is **Gtk::Main:init**. Now I need to figure out how to connect on bus signals... I am tired now I'll look into tomorrow :D

---

