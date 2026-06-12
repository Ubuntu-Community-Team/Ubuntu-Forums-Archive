---
title: "Glade table"
date: 2012-02-13
forum: Programming Talk
---

### Post by Frozen Forest on 2012-02-13
How do you add an table in gtk, been looking for it but can't find it. Attached an image with the options that are available, is there something i missed, it's in Swedish but I think the images are the same. Looking for table where it's possible to sort by column, similar to how deluge handle torrent in there gtk ui.

---

### Post by deathadder on 2012-02-14
You'd need to make use of a TreeView and ListStore and then, if I remember correctly, write a handler to sort the column. Don't quote me on that though!

[http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm](http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm)

---

