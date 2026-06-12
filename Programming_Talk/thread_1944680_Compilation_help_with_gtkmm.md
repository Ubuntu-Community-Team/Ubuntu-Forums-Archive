---
title: "Compilation help with gtkmm"
date: 2012-03-21
forum: Programming Talk
---

### Post by mikeglaz on 2012-03-21
I'm trying to learn gtkmm. I tried the tutorial on their website which looks like this:
```

#include <gtkmm.h>

int main(int argc, char *argv[])
{
  Glib::RefPtr<Gtk::Application> app =
    Gtk::Application::create(argc, argv,
      "org.gtkmm.examples.base");

  Gtk::ApplicationWindow window;

  return app->run(window);
}

```

Now I compile with this command (the one suggested in the tutorial): g++ simple.cc -o simple `pkg-config gtkmm-3.0 --cflags --libs`

and get the following errors:
simple.cc: In function ‘int main(int, char**)’:
simple.cc:5:16: error: ‘Application’ is not a member of ‘Gtk’
simple.cc:5:16: error: ‘Application’ is not a member of ‘Gtk’
simple.cc:5:32: error: template argument 1 is invalid
simple.cc:5:38: error: invalid type in declaration before ‘=’ token
simple.cc:6:10: error: ‘Gtk::Application’ has not been declared
simple.cc:9:3: error: ‘ApplicationWindow’ is not a member of ‘Gtk’
simple.cc:9:26: error: expected ‘;’ before ‘window’
simple.cc:11:13: error: base operand of ‘->’ is not a pointer
simple.cc:11:19: error: ‘window’ was not declared in this scope

mike

---

### Post by SevenMachines on 2012-03-22
My guess would be that the gtkmm .pc file isnt found, try running 
```
 $ pkg-config gtkmm-3.0 --cflags --libs
```on its own. Is it full of libs and flags? or is it things like
```
 Package gtkmm-3.0 was not found in the pkg-config search path.
```If the latter then you need to
```
$ sudo apt-get install libgtkmm-3.0-dev
```

---

### Post by flyboy on 2012-03-22
Which version of gtkmm do you have installed? Although the tutorial shows the Gtk::Application version, this was (will be!) introduced in gtkmm 3.4:

[http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Application.html]("http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Application.html")

Until then, you need Gtk::Main():

[http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Main.html]("http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Main.html")

Rgds.,
Paul

---

### Post by flyboy on 2012-03-22
Actually, 3.4 is not yet released - Looks like next week from gnome.org:

[http://https://live.gnome.org/ThreePointThree]("http://https://live.gnome.org/ThreePointThree")

---

### Post by HasanYavuzOZDERYA on 2012-03-22
> **flyboy said:**
> Which version of gtkmm do you have installed? Although the tutorial shows the Gtk::Application version, this was (will be!) introduced in gtkmm 3.4:

[http://http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Application.html](http://http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Application.html)

Until then, you need Gtk::Main():

[http://http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Main.html](http://http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Main.html)

Rgds.,
Paul

Thank you, that helped..

---

### Post by flyboy on 2012-03-23
> **HasanYavuzOZDERYA said:**
> Thank you, that helped..

I just fixed the links in the original email - I should have checked them after saving the message - sorry!

---

