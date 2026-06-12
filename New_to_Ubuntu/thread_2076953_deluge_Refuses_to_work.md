---
title: "deluge Refuses to work"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by suarez on 2012-10-27
pleaz help ihave a big problem
deluge hi won't start 

this is the message from terminal

(deluge:25171): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
[ERROR   ] 14:09:27 gtkui:69 Unable to initialize gettext/locale!
[ERROR   ] 14:09:27 gtkui:70 unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py", line 58, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.7/locale.py", line 539, in setlocale
    return _setlocale(category, locale)
Error: unsupported locale setting
/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py:179: GtkWarning: locale not supported by C library
  self.gnome_prog = gnome.init("Deluge", deluge.common.get_version())
[ERROR   ] 14:09:28 daemon:107 Unable to initialize gettext/locale: unsupported locale setting
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted (core dumped)

pleaz any help
:'(
:-(:(

---

### Post by circlemaster on 2012-10-27
What happens if you type in terminal:
```
LANGUAGE=en:us
deluge
```

---

### Post by suarez on 2012-10-27
(deluge:18615): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
[ERROR   ] 14:44:01 gtkui:69 Unable to initialize gettext/locale!
[ERROR   ] 14:44:01 gtkui:70 unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py", line 58, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.7/locale.py", line 539, in setlocale
    return _setlocale(category, locale)
Error: unsupported locale setting
/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py:179: GtkWarning: locale not supported by C library
  self.gnome_prog = gnome.init("Deluge", deluge.common.get_version())
[ERROR   ] 14:44:03 daemon:107 Unable to initialize gettext/locale: unsupported locale setting
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted (core dumped)

---

### Post by suarez on 2012-10-27
:confused::(
pleaz any help!!!!!

---

### Post by suarez on 2012-10-27
Please help I am stuck
:(

---

