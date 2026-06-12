---
title: "newbie python/glade error"
date: 2005-11-07
forum: Programming Talk
---

### Post by stimpack on 2005-11-07
Designed a dialog in glade and trying to display it with

```

#!/usr/bin/python
import gtk
import gtk.glade
#Give glade file path
fname = 'gtkdialog.glade'
# create widget tree ...
App = gtk.glade.XML(fname)
entry1 = glade.get_widget('label1')
App.signal_autoconnect(locals())
gtk.main()

```

but get the following error

```
Traceback (most recent call last):
  File "./go.py", line 8, in ?
    entry1 = glade.get_widget('label1')
NameError: name 'glade' is not defined
```

I have installed:

python-glade2
python-gtk2
python-gnome2
glade-2
libglade2-0

any ideas what I am missing to casue this error?

---

### Post by Retrix on 2005-11-07
Change this:

[QUOTE=stimpack]
```

entry1 = glade.get_widget('label1')

```
[/QUOTE]

to:

```

entry1 = **gtk**.glade.get_widget('label1')

```

---

### Post by ow50 on 2005-11-07
[QUOTE=stimpack]```
Traceback (most recent call last):
  File "./go.py", line 8, in ?
    entry1 = glade.get_widget('label1')
NameError: name 'glade' is not defined
```[/QUOTE]

```

#!/usr/bin/python
import gtk
import gtk.glade
#Give glade file path
fname = 'gtkdialog.glade'
# create widget tree ...
App = gtk.glade.XML(fname)
entry1 = **App**.get_widget('label1')
App.signal_autoconnect(locals())
gtk.main()

```

You're getting the widget from the object created from your Glade XML file, not from any generic module, be it glade or gtk.glade.

---

### Post by stimpack on 2005-11-07
That fixs it, thanks for your swift replies!.

---

