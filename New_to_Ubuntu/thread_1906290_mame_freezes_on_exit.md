---
title: "mame freezes on exit"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-08
Hi,

Ubuntu 11.10 64bit,

mame freezes on exit how can I fix this?

Thanks

---

### Post by hopelessone on 2012-01-08
*bump*

---

### Post by hopelessone on 2012-01-09
```
blade@oneiric:/mnt/hdd_4/Games/MAME/Roms$ mame 1942
Debug Build: Disabling input grab for -debug
WARNING: Couldn't find/open TrueType font ui.bdf, using MAME default

(mame:2889): Gtk-CRITICAL **: IA__gtk_window_resize: assertion `height > 0' failed

(mame:2889): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(mame:2889): Gtk-CRITICAL **: IA__gtk_window_get_position: assertion `GTK_IS_WINDOW (window)' failed

(mame:2889): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(mame:2889): Gtk-CRITICAL **: IA__gtk_window_get_size: assertion `GTK_IS_WINDOW (window)' failed
Killed

```

---

### Post by hopelessone on 2012-01-09
```
#
# VIDEO OPTIONS
#
video                     soft
```

Changing the video from opengl to soft did it..

---

