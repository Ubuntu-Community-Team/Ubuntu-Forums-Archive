---
title: "Dash Home and Jockey-GTK crash 12.04"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by nucleus2 on 2014-02-26
Greetings all,

I'm a green user to ubuntu having recently installed 12.04 by method of USB.

Whenever I click on the Dash Home button, the desktop crashes (and then relaunches, some of the time). This isn't always immediate, sometimes it allows me to type a couple of letters into the application search bar.
I have since changed to the gnome desktop.

Furthermore, whenever trying to check for additional drivers (I have a STRONG feeling my problems are Graphics driver related), the application crashes. In other words, when I run ```
sudo jockey-gtk
```, I get the following error output: ```
(jockey-gtk:2821): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:2821): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 280, in update_tree_model
    pixbuf = theme.load_icon('jockey-enabled', 16, 0)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Icon 'jockey-enabled' not present in theme

```

Please note that I have the latest NVIDIA drivers installed via ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
```

```
lspci
``` gives: ```
01:00.0 VGA compatible controller: NVIDIA Corporation GF114M [GeForce GTX 580M] (rev a1)
```

I am very willing to post any more information if required.

EDIT: I should probably add I am dual booting Ubuntu 12.04 x64 and Windows 7 x64

---

### Post by sandyd on 2014-02-26
have you tried just
```
jockey-gtk
```
or
```

gksu jockey-gtk
```

---

### Post by nucleus2 on 2014-02-26
When I used just: ```
jockey-gtk
``` The 2 Gtk-CRITICAL errors occur, and then the progress window for "Checking for Additional Drivers" appeared. After awhile, the window crashes causing the traceback output. 
A crash report comes up reporting that jockey-gtk closed unexpectedly. A further dialogue window appears: ```
/usr/local/lib/libpangoft2-1.0.so.0.3400.1/usr/local/lib/libpango-1.0.so.0.3400.1
/usr/local/lib/libgmodule-2.0.so.0.3600.4
/usr/local/lib/libatk-1.0.so.0.20809.1
/usr/local/lib/libz.so.1.2.8
/usr/local/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
/usr/local/lib/libgobject-2.0.so.0.3600.4
/usr/local/lib/libharfbuzz.so.0.926.0
/usr/local/lib/libgio-2.0.so.0.3600.4
/usr/local/lib/pango/1.8.0/modules/pango-basic-fc.so
/usr/local/lib/libgdk_pixbuf-2.0.so.0.2800.2
/usr/local/lib/libexpat.so.1.6.0
/usr/local/lib/libffi.so.6.0.1
/usr/local/lib/libpangocairo-1.0.so.0.3400.1
/usr/local/lib/libpng16.so.16.9.0
/usr/local/lib/libfontconfig.so.1.8.0
/usr/local/lib/libfreetype.so.6.11.1
/usr/local/lib/libglib-2.0.so.0.3600.4


It is highly recommended to check if the problem persists without those first.

```
Intuitively, the next step is to remove those packages, but I need most of them for [OpenCV]("http://opencv.org/"), [PCL]("http://pointclouds.org/"), and [ROS]("http://www.ros.org/")-Hydro depend on them. 
What do?

---

### Post by nucleus2 on 2014-02-28
bump?

---

