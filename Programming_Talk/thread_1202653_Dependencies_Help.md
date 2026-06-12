---
title: "Dependencies Help"
date: 2009-07-02
forum: Programming Talk
---

### Post by Levo on 2009-07-02
What dependencies are required for a program that is:
-half a bash script (uses zenity for dialogs)
-half a python/pygtk script (displays a dialog)
-no other commands are used

zenity, nautilus(it is used to open folders), python, python-gtk2 ?

Or are there more that I need to add?

---

### Post by smartbei on 2009-07-02
Well, unless you want it to use nautilus no matter what, why not read from gconf and find out what the user's file manager is? the key seems to be at /desktop/gnome/session/required_components/filemanager
Try this:
```

import gconf
client = gconf.client_get_default()
print client.get_string("/desktop/gnome/session/required_components/filemanager")

```
If gconf throws an exception, install python-gconf.

---

