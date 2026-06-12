---
title: "Can I modify through shell &quot;system--preferences--appearance--interface&quot; settings?"
date: 2009-10-27
forum: Programming Talk
---

### Post by giuspen on 2009-10-27
Is it possible to write a bash/python script to edit the ubuntu/gnome settings:

system->preferences->appearance->interface

such as the checkbox "Show icons in menus" or the combobox "Toolbar button labels"?

Thanks in advance.

---

### Post by giuspen on 2009-10-30
if anybody interested, using python a possible solution is:

[PHP]#!/usr/bin/env python

import subprocess

subprocess.call("gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool 1", shell=True)[/PHP]

---

### Post by kaibob on 2009-10-30
Most of these settings are in gconf repository. For example,

```
/desktop/gnome/interface/menus_have_icons
```

The following is an example of how command-line changes can be made to gconf keys:

```
gconftool-2 --type bool --set /apps/panel/global/locked_down true
```

---

### Post by diesch on 2009-10-31
> **giuspen said:**
> if anybody interested, using python a possible solution is:

[php]#!/usr/bin/env python

import subprocess

subprocess.call("gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool 1", shell=True)[/php]

If all you want to do is to run a program you better use the shell instead a Python:

```
#/bin/sh
gconftool-2 --set /desktop/gnome/interface/menus_have_icons --type bool true

```If you use Python to set GConf properties you may want to use [easygconf]("http://www.florian-diesch.de/software/easygconf/"):

```
#!/usr/bin/env python

import easygconf

d = easygconf.GConfDict('/desktop/gnome/interface/')
d['menus_have_icons'] = True

```

---

