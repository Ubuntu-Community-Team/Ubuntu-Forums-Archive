---
title: "[SOLVED] Cannot find glade file for referencer"
date: 2007-11-15
forum: Programming Talk
---

### Post by Curtisc on 2007-11-15
I am trying to compile [referencer]("https://launchpad.net/referencer") from source, but after I run autogen.sh and make, I get the following error upon launching the program:

```
Utility::findDataFile: couldn't find file 'preferences.glade'
(referencer:24639): libglade-WARNING **: could not find glade file ''
terminate called after throwing an instance of 'Gnome::Glade::XmlError'
Aborted (core dumped)

```

Before I go bugging the developers about this error, is there a normal solution to this type of problem?  I'm guessing I need to edit some path somewhere, but I don't know where.

---

### Post by Curtisc on 2007-11-15
Never mind... I just need to run it with the absolute path, not from the directory.

---

