---
title: "Glade interface designer 3.4.0"
date: 2008-01-14
forum: Programming Talk
---

### Post by superhac007 on 2008-01-14
I just loaded up the Glade interface designer 3.4 version and it works, but when I reload one of my gui glade XML configuration files it does not render the visual editor part?  The visual editor part only works on new files.  Once their saved the file is reload, but the UI is not visually render.    

Anyone else having this problem?

Thanks

---

### Post by superhac007 on 2008-01-17
Well I finally figured it out myself.  It seems that libglade0 is needed to rerender the glade xml files when your opening a saved glade.xml file.  I would think this would be be a dependency of glade3????

Anyway just install libglade0 and it works.

from libglade0:

This library allows you to load user interfaces in your program, which are
stored externally.  This allows alteration of the interface without
recompilation of the program.

The interfaces can also be edited with GLADE.

---

### Post by superhac007 on 2008-01-18
I have to take back what I said fixed it!!  It seems when you open a saved glade xml file you need to double click on the "Top Window" of your GUI in the hierarchy view to get it to display the visual editor!!!

---

