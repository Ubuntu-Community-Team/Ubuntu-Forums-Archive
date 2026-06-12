---
title: "[GTK#] Setting font for tree view at once?"
date: 2011-11-21
forum: Programming Talk
---

### Post by Vladimir Hidalgo on 2011-11-21
I would like to know if there is some way to set the font for the tree view cells at once?.

---

### Post by crdlb on 2011-11-21
I'm not sure about the specific syntax for GTK#, but you can set properties directly on the CellRendererText in addition to mapping properties to model columns.

---

### Post by Vladimir Hidalgo on 2011-11-21
I do initialize the tree view this way:


```
		treeTiquetes.AppendColumn("Inicio",new Gtk.CellRendererText(),"markup",0);
		treeTiquetes.AppendColumn("O",new Gtk.CellRendererText(),"markup",1);
		treeTiquetes.AppendColumn("D",new Gtk.CellRendererText(),"markup",2);
		treeTiquetes.AppendColumn("Notas",new Gtk.CellRendererText(),"markup",3);

```


What parameters do I have to put into Gtk.CellRendererText()?

Thank you!

---

### Post by Vladimir Hidalgo on 2011-11-21
Thanks for hint, I've succeed by creating an Gtk.CellRendererText() object and setting there the font properties.

Thank you very much!

---

