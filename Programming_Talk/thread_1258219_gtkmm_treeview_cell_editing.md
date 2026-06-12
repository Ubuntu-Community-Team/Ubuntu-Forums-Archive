---
title: "gtkmm treeview cell editing"
date: 2009-09-04
forum: Programming Talk
---

### Post by bubba_169 on 2009-09-04
In gtkmm there are signals for the cell renderer to pick up when editing a cell has started or has been cancelled but I cant seem to find one for if the editing has stopped successfully.

Do I still use the cancelled signal or is there an alternative?
Thanks

---

### Post by bubba_169 on 2009-09-05
Found it! I've found you can use the signal_edited from cellrenderertext.

---

