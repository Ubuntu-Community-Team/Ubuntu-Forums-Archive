---
title: "PyGTK IDE"
date: 2005-02-15
forum: Programming Talk
---

### Post by nocturn on 2005-02-15
Does anyone know a good IDE for PyGTK?  
One that has versions for Windows too would be nice (for use at my job, at home it is Linux only).

---

### Post by Chris Ferrell on 2005-02-15
I guess you mean an IDE written in PyGtk since you can use any IDE to write PyGtk programs.  

This one is not near ready for production use yet, but with only 8 files for the whole thing, is itching for someone to contribute to it.  [http://www.galilea.cl/snmartin/grad/](http://www.galilea.cl/snmartin/grad/)

You could also use SPE, which uses wxPython and looks great on Hoary since we've got gtk2.x under the hood yet, has cool stuff like pop-up code completion, and pop-up docs, but is very buggy on my system.  I had multiple crashes not doing much.

---

### Post by nocturn on 2005-02-15
[QUOTE=Chris Ferrell]I guess you mean an IDE written in PyGtk since you can use any IDE to write PyGtk programs.  

This one is not near ready for production use yet, but with only 8 files for the whole thing, is itching for someone to contribute to it.  [http://www.galilea.cl/snmartin/grad/](http://www.galilea.cl/snmartin/grad/)

You could also use SPE, which uses wxPython and looks great on Hoary since we've got gtk2.x under the hood yet, has cool stuff like pop-up code completion, and pop-up docs, but is very buggy on my system.  I had multiple crashes not doing much.[/QUOTE]

I really mean an IDE to create PyGTK programs, preferably with an interface designer.
Boa Constructor looks nice for WxPython programs.

---

### Post by gazum on 2005-02-15
[QUOTE=nocturn]I really mean an IDE to create PyGTK programs, preferably with an interface designer.
Boa Constructor looks nice for WxPython programs.[/QUOTE]

Glade is a visual interface designer for Gtk. It creates an XML description of a form and widgets in a .glade file. Python2.3-glade2 library allows you to use this file and write custom event handlers in python. See examples in /usr/share/doc/python2.3-glade2/examples/glade/ folder.

Packages required: glade2, python2.3-glade2.

---

### Post by randy on 2005-02-20
You could also try using Gazpacho, instead of Glade.  I'm not sure if the files are compatible with glade.  It's got an easier to use interface and things like under and redo support.

---

### Post by encompass on 2007-02-20
glade works VERY well with python.  I use it every day.  Many good tutorials to get you started.

---

### Post by gh0st on 2007-02-20
I use SPE mostly, it's got it's bugs but I quite like it. It has a Glade designer built in as well. If you look on the "tools" menu there is an option "design a GUI with wxGlade". That opens the Glade designer for you.

It's a nice all round IDE I think but like I say it's not perfect. Then again what it? :)

---

### Post by stani on 2007-02-23
If you install the python-wxtools, you can also use XRCed from SPE, which is another good GUI editor:

```
sudo apt-get install spe python-wxtools python-xml
```

---

