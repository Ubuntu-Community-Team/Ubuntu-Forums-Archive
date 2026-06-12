---
title: "Python - Glade - Distribution"
date: 2008-05-26
forum: Programming Talk
---

### Post by Ziggy72 on 2008-05-26
I'm new to python and Glade so this may be a stupid question - I hope not.

I've written a python program and used Glade to create the gui. I use Komodo Pro for program development and everything works fine in Komodo when I'm running and debugging the program. However, if I take both the .py and .glade file out of the IDE and put them in a remote directory together and then try to run the program (after making the .py file executable) nothing happens.

So my question is, if I create a program using python and Glade, how can I distribute it to others, preferably as a single executable file?

Any help will be much appreciated. TIA.

---

### Post by Quikee on 2008-05-27
You can put the content of the .glade file into the .py file as a (multi-line) string variable and create the glade.XML object with gtk.glade.xml_new_from_buffer(...) instead of invoking the constructor with .glade file as input parameter. With this you have only one file but you will loose the freedom to quickly tune the looks with glade. 

See [here]("http://www.pygtk.org/docs/pygtk/class-gladexml.html") for glade documentation. 

Anyway .. your problem is probably only that the path defined in the glade in the glade.XML construction is not found when you move both files.

---

