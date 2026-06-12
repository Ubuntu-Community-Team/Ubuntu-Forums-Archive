---
title: "Simple hello world gtkmm app fail."
date: 2012-01-26
forum: Programming Talk
---

### Post by sajimon on 2012-01-26
Hello, i have this gtkmm application example from gnome development documentation

i put it all in one file, here is a code
[http://dpaste.com/693447/](http://dpaste.com/693447/)

when i run application i got plenty of error massages 

```

(process:28961): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:28961): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:28961): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:28961): GLib-GObject-WARNING **: cannot add class private field to invalid type '<invalid>'

(process:28961): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:28961): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:28961): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:28961): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(process:28961): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:28961): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(process:28961): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()
```

i looks like Gtk::Main kit(); wasn't called or something.
I'm using gtkmm-3

---

### Post by gmargo on 2012-01-26
According to this tutorial: [http://developer.gnome.org/gtkmm-tutorial/3.0/sec-helloworld.html.en](http://developer.gnome.org/gtkmm-tutorial/3.0/sec-helloworld.html.en)
you are calling **GTK:: Main kit()** and **Gtk::Main::run()** incorrectly.

Try this for your **main()** routine:
```

int main(int argc, char** argv)
{
        Gtk::Main kit(argc, argv);

        HelloWorld hw;

        Gtk::Main::run(hw);

        return 0;
}

```BTW, you could have put your code here, in a code block.  Much better for future reference than an external paste site.

---

### Post by sajimon on 2012-01-27
Hey, thanks for reply.

I'm afraid thats not it, kit() parameters are optional, but ofcourse I checked it anyway - didn't helped.

---

### Post by t1497f35 on 2012-01-27
For some reason you need to pass argc & argv:

> 
int main(int argc, char *argv[]) {
    Gtk::Main kit(argc, argv);
...


Also, don't forget to pass the Gtk::Window "hw" to Gtk::Main::run():
> 
Gtk::Main::run(hw);


---

