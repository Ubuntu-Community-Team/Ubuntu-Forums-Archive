---
title: "Could not find the file “/etc/hal/fdi/policy/99-x11-wizardpen.fdi”."
date: 2014-06-27
forum: New to Ubuntu
---

### Post by bluesky541 on 2014-06-27
I've been trying to make a .fdi file following these instruction on installing the wizardpen ([http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260)),
[COLOR=#000000]I type in the terminal:[/COLOR]```
gksudo gedit  /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```
[COLOR=#000000]Then the text editor opens, I write in it, then click the save button, but it says [/COLOR][COLOR=#ff0000]Could not find the file “/etc/hal/fdi/policy/99-x11-wizardpen.fdi”.
[/COLOR][COLOR=#000000]And while I write in the empty file, it starts writing in the terminal:[/COLOR]```
(gedit:2817): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(gedit:2817): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```
[COLOR=#000000]Am I doing something wrong? How should I create a .fdi file? I tried saving it as 'all text files', but then it saves it as an XML document....
I'm using ubuntu 14.04 LTS, 32bit. Please help..
[/COLOR]

---

### Post by cariboo on 2014-06-28
The /etc/hal directory no longer exists as hal is no longer used. The tutorial you are using is from 2009, I'd suggest you try to find one quite a bit newer, as much has changed in the last 5 years.

---

