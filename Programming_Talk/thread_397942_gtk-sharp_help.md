---
title: "gtk-sharp help"
date: 2007-03-31
forum: Programming Talk
---

### Post by rekahsoft on 2007-03-31
Hi all, i have been learning gtk-sharp and for some reason i cannot get gtk2 widgets...all the widgets look gtk-1.x...here is some simple code:```
using System;
using Gtk;

class GUI : Window {

     private int click_count = 0;
     
     public GUI() : base("GUI") {
          Application.Init();
          this.SetDefaultSize(100, 100);
          this.DeleteEvent += delegate {
               Application.Quit();
          };

          Button btn = new Button("Click Me");
          btn.ButtonPressEvent += delegate {
               ++click_count;
               btn.Label = "Clicked " + click_count + " times";
          };
          this.Add(btn);
          this.ShowAll();
          Application.Run();
     }

     public static void Main(string[] args) {
          new GUI();
     }
}
```Then i compile with:```
mcs GUI.cs -pkg:gtk-sharp-2.0
```I can post a screenshot if needed but it saying that the widgets look gtk-1.x is just as good. Thanks for the help :D

Edit: Also i am getting gtk warnings in the terminal when i run it causing Events (besides DeleteEvent) to not function...here is the gtk warning:```
(Clicker.exe:22013): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(Clicker.exe:22013): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(Clicker.exe:22013): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
```Every time the button is clicked i get:```
(Clicker.exe:22013): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
```

---

### Post by frychiko on 2007-04-12
Heh I just started with GTK# myself a couple of days ago... anyway..

You're trying to initiate and start up GTK within the window object itself, you must call them from the main application, not within a gui object.

```
using System;
using Gtk;

class GUI : Window {

     private int click_count = 0;
     
     public GUI() : base("GUI") {
          this.SetDefaultSize(100, 100);
          this.DeleteEvent += delegate {
               Application.Quit();
          };

          Button btn = new Button("Click Me");
          btn.ButtonPressEvent += delegate {
               ++click_count;
               btn.Label = "Clicked " + click_count + " times";
          };
          this.Add(btn);
          this.ShowAll();

     }

     public static void Main(string[] args) {
        **  Application.Init();**
          new GUI();
          **Application.Run();**
     }
}
```

---

### Post by rekahsoft on 2007-04-12
ok...cool i did not know that :D

---

