---
title: "[SOLVED] Unable to edit Menu"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by pravin03 on 2008-08-04
Unable to edit menu[In Hardy(8.04)] when right clicking and selecting Edit menu.
It is not possible from system -preferences-Main menu.

---

### Post by philinux on 2008-08-04
> **pravin03 said:**
> Unable to edit menu[In Hardy(8.04)] when right clicking and selecting Edit menu.
It is not possible from system -preferences-Main menu.


system -preferences-Main menu then
Right click your chosen menu item and select properties.

---

### Post by drs305 on 2008-08-04
You might also get there with:
```
alacarte
```

---

### Post by pravin03 on 2008-08-04
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ml_IN

---

### Post by pravin03 on 2008-08-05
problem was due to a language support issue.I enabled language support from system->Admnstn->Language Support.

Thanking all.

---

