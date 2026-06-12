---
title: "Python GUI creator"
date: 2005-01-27
forum: Programming Talk
---

### Post by python on 2005-01-27
Does anyone know of any Delphi-style python form creator? Something like pythonworks?

I have a big A-level database project on my hands. Not sure I wanna tk the thing by hand. Doesn't have to be tk though.

---

### Post by EdCrypt on 2005-01-27
Maybe you shold try  Glade. It generates a xml file (.glade) that  can be used in your project.

```
import gtk, gtk.glade

dic = { "gtk_main_quit" : gtk.main_quit }

gladefile = gtk.glade.XML("empty.glade")
gladefile.signal_autoconnect(dic)

gtk.main()
``` 

More in the [PyGTK Site](http://pygtk.org)

---

### Post by Quest-Master on 2005-01-27
[QUOTE=EdCrypt]Maybe you shold try  Glade. It generates a xml file (.glade) that  can be used in your project.

```
import gtk, gtk.glade

dic = { "gtk_main_quit" : gtk.main_quit }

gladefile = gtk.glade.XML("empty.glade")
gladefile.signal_autoconnect(dic)

gtk.main()
``` 

More in the [PyGTK Site](http://pygtk.org)[/QUOTE]
 wxGlade is also a nice choice in case you want to use wxWidgets instead of GTK (cross-platform).

---

### Post by python on 2005-01-27
[QUOTE=Quest-Master]wxGlade is also a nice choice in case you want to use wxWidgets instead of GTK (cross-platform).[/QUOTE]
 That's cool. Problem solved really. When I heard we had to do our projects in Delphi, I point blank refused ;-) This is going to make it a lot easier. Thanks a lot.

---

