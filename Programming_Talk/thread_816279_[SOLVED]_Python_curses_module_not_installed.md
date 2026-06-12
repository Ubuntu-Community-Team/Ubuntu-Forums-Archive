---
title: "[SOLVED] Python curses module not installed"
date: 2008-06-02
forum: Programming Talk
---

### Post by Paul Miller on 2008-06-02
I've got a clean install of Hardy running inside VirtualBox, and, for some reason, the curses module is not installed for Python.  Any idea what I need to do to fix this?

Thanks!

---

### Post by geirha on 2008-06-02
You need the python2.5 package installed, not sure whether that package is installed by default or not, though I would've imagined it was.

---

### Post by Paul Miller on 2008-06-02
> **geirha said:**
> You need the python2.5 package installed, not sure whether that package is installed by default or not, though I would've imagined it was.

aptitude search python2.5 | grep ^i

shows these packages installed: 

i   python2.5                   
i A python2.5-dev
i A python2.5-doc       
i   python2.5-minimal 

Thanks for trying, though. :-)

---

### Post by geirha on 2008-06-02
Then the curses module should be installed:
```
$ dpkg -L python2.5| grep curses
/usr/lib/python2.5/curses
/usr/lib/python2.5/curses/__init__.py
/usr/lib/python2.5/curses/ascii.py
/usr/lib/python2.5/curses/has_key.py
/usr/lib/python2.5/curses/panel.py
/usr/lib/python2.5/curses/textpad.py
/usr/lib/python2.5/curses/wrapper.py
/usr/lib/python2.5/lib-dynload/_curses.so
/usr/lib/python2.5/lib-dynload/_curses_panel.so

```

---

### Post by Paul Miller on 2008-06-02
Well, I still don't know what originally caused the problem: all those files were installed and in the proper places, yet I still got an ImportError trying to import curses.

Since this was just a VM used for testing purposes, I wiped it and reinstalled.  Whatever the problem was, that solved it.  

Thanks anyway to everyone who tried to help.

---

