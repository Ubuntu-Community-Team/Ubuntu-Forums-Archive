---
title: "New to programming/Python. Compiling pyGTK error"
date: 2007-03-07
forum: Programming Talk
---

### Post by WalmartSniperLX on 2007-03-07
Hi. Im new to programming (learning with Python) and I just downloaded the pyGTK source and barely got to run the configure script for compiling and I ran into this error :

```

checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

What do I do at this point?

---

### Post by WalmartSniperLX on 2007-03-07
DARN IT I guess this should have gone in the sub section for compiling :mad:  Sorry

---

### Post by WW on 2007-03-07
Installing from the source will give you the latest version, but to get started quickly, you could install the package **python-gtk2**.

---

### Post by duff on 2007-03-07
You should already have it. Does running ```
# python -c 'import pygtk; print pygtk._get_available_versions()'
``` from your shell work?

---

### Post by WalmartSniperLX on 2007-03-07
It says I already have python-gtk2. Is it the same thing? 

The output for:

```
 
python -c 'import pygtk; print pygtk._get_available_versions()'

```

Is:

```

{'2.0': '/usr/lib/python2.5/site-packages/gtk-2.0'}

```

---

### Post by po0f on 2007-03-07
WalmartSniperLX,

Yes, a lot of programs in Ubuntu are written using the Python/PyGTK combination.  It comes installed standard.  :)

---

### Post by duff on 2007-03-07
> **WalmartSniperLX said:**
> It says I already have python-gtk2. Is it the same thing? 

The output for:

```
 
python -c 'import pygtk; print pygtk._get_available_versions()'

```

Is:

```

{'2.0': '/usr/lib/python2.5/site-packages/gtk-2.0'}

```
Great! Now run 'python' and type these commands:
```
>>> import gtk
>>> w = gtk.Window()
>>> w.set_title('Hello World!')
>>> w.connect('destroy', gtk.main_quit)
>>> w.show()
>>> gtk.main()
```

---

