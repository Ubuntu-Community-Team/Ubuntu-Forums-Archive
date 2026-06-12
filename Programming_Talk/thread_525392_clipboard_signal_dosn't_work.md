---
title: "clipboard signal dosn't work?"
date: 2007-08-14
forum: Programming Talk
---

### Post by tech4web on 2007-08-14
i do it with qt but it  seems that qt can not handle this!
i want any more global signal that send clipboard change signal to my qt app?
this is my code but it not working when text selected from a gnome application!

connect(QApplication::clipboard(),SIGNAL(selectionChanged()),this,SLOT(sltGetMeanBySelection()));

but in any kde app it work fine.

i want alternate way in x11 or ... ?

---

### Post by tech4web on 2007-08-15
help please!!!!!!!!!!!!!!!!!!!!

---

