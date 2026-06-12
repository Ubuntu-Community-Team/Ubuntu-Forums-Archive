---
title: "warning while creating etc/lightdm/lightdm.conf file"
date: 2018-05-10
forum: New to Ubuntu
---

### Post by sdeflabofficial on 2018-05-10
HI,
We currently have Ubuntu 16.04 LTS installed. Running it with an Lxde destkop environment.

We've run into this GTK warning whenever we are using gedit.

If we start typing in a gedit window, or save it, this output appears on the screen:

(gedit:5090): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:  org.freedesktop.DBus.Error.ServiceUnknown: The name  org.gnome.SessionManager was not provided by any .service files

Is this warning affect  other process?
 
Is it a serious issue , is there a simple workround where this Gtk-warning  can be suppressed?

Please help us
Thanks in advance

---

### Post by dino99 on 2018-05-10
'warning' is not an error; as it only warns, a kind of dev reminder for a future todo work.
That warning is a long standing warning logged, but fully harmless. :D

---

### Post by tinylagarto on 2018-05-10
Not a specialist here with Gtk but I assume you can just ignore that message. It is harmless. 

You use sudo to open Gedit. It would be better opening the file with something like nano or vim if you are root and editing system files.

---

