---
title: "Color chooser does nothing....?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by K-Drew on 2008-08-30
Hello,

This is my first time posting in the Ubuntu forum, as most of the time the answers to my questions were already posted.  I also didn't know enough to answer anyone else's questions. :-)

I have Ubuntu 8.04 installed with Compiz Fusion and Emerald.  I'm trying to change the color of the panel font, using color chooser.  But when I press "apply" it does nothing.

No one else seems to be having any issues with it....and since with Hardy editing the .gtk2.0 file does not work, and color chooser doesn't work, I guess I'm stuck.  Anyone else have this problem?

---

### Post by gmxgeek on 2008-08-30
Have you tried restart Xserver after applying?

---

### Post by K-Drew on 2008-08-30
Doing a kill of the gnome panel doesn't work, nor does restarting X.  What's the deal?  

Also, when I hit info on the color chooser I get this: 

Version information:
  Compiled on GTK+ version 2.12.7
  Running on GTK+ version 2.12.9

Environment variables:
  GTK_PATH is not set.
  GTK_EXE_PREFIX is not set.
    GTK+ will search: $libdir/lib/gtk-2.0/...
  GTK_DATA_PREFIX is not set.
    GTK+ will search: $prefix/share/themes
  GTK2_RC_FILES is not set.
    GTK+ will read: $sysconfdir/gtk-2.0/gtkrc and ~/.gtkrc-2.0

General settings:
  Language is en-us.
  Theme is Human.
  Default font is Sans 10.
  Icon theme is Human.
  Key theme is Default.
  Xft antialiasing is turned on.
  Xft is set to 96.00 DPI.
  gtk_rc_get_default_files(): /etc/gtk-2.0/gtkrc

Display name is :0.0 and has 1 screens.
  Screen 0: 1024x768 on 1 monitors.
  Window manager is compiz.
    Monitor 0: 0,0 1024x768

Style information from a button:
  Focus width 1, focus pad 1.
  Default border (0,0,0,0)
  Normal foreground (4112,4112,4112), background (61423,60395,59367).

Font information from a default label:
  Font: Sans
  Size: 10240 (10 pixels)
  Approximate char width: 6380 (6 pixels)
  Approximate digit width: 8192 (8 pixels)

Global font information:
  There are 92 font families.
  There are a total of 373 faces in all families.

---

