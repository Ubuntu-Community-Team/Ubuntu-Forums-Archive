---
title: "[Gtk3] What kind of features are these?"
date: 2012-09-22
forum: Programming Talk
---

### Post by bird1500 on 2012-09-22
Hi,
Gtk::Application requires *APPLICATION_HANDLES_COMMAND_LINE* to let you access argc, argv which one can access anyway, so if you don't pass that flag, when you access argv or so glibmm throws an error:
> GLib-GIO-CRITICAL **: This application can not open files.What kind of feature or protection is this? What's the genius idea behind this?

Also, Gtk::ApplicationWindow seems useless, anyone actually using it? It throws an error if you try using it. I've seen people misusing it in the documentation of gtk3 itself only to be replaced by Gtk::Window to make the example source code compile & run.

---

### Post by juancarlospaco on 2012-09-22
Been there, see more like that, on Python too, i think it dont have a solution, but workarounds.

I dont investigate too much, good luck, from the Qt5 side of the world :)

---

### Post by SledgeHammer_999 on 2012-09-22
Could you provide sample code that shows this warning/behavior?

Could you please expand more on the GtkApplicationWindow problem with example code or links to said documentation?

---

### Post by bird1500 on 2012-09-22
> **SledgeHammer_999 said:**
> Could you provide sample code that shows this warning/behavior?

Could you please expand more on the GtkApplicationWindow problem with example code or links to said documentation?

Here's a screenshot, I commented out APPLICATION_HANDLES_COMMAND_LINE, compiled & ran without any args and it ran fine, but when I ran it with args (just "sdf" for the sake of brevity) it yields an error/warning to the terminal. To not get errors/warnings one has to supply that argument.

As to the errors using ApplicationWindow here's a discussion:
[http://stackoverflow.com/questions/10756770/meaning-of-glib-gio-critical-assertion-error](http://stackoverflow.com/questions/10756770/meaning-of-glib-gio-critical-assertion-error)

The last suggestion from that discussion:
Gtk::ApplicationWindow window(app);
doesn't solve the issue.

BTW, using the Application class and making your main window disappear without exiting the app was another interesting journey!

---

