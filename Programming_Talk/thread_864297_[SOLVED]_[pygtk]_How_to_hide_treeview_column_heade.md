---
title: "[SOLVED] [pygtk] How to hide treeview column header?"
date: 2008-07-19
forum: Programming Talk
---

### Post by days_of_ruin on 2008-07-19
Glade does it.But how?

---

### Post by mssever on 2008-07-19
> **days_of_ruin said:**
> Glade does it.But how?
```
your_treeview_instance.set_headers_visible(False)
```
See DevHelp.

---

### Post by days_of_ruin on 2008-07-19
> **mssever said:**
> ```
your_treeview_instance.set_headers_visible(False)
```
See DevHelp.

Thanks.I was looking under treeviewcolumn in the pygtk ref man.
btw I know exactly how you made you avatar
:lolflag:

---

### Post by mssever on 2008-07-19
> **days_of_ruin said:**
> 
btw I know exactly how you made you avatar
My first experiment with Inkscape...

EDIT:I also noticed that your location is similar to mine. :)

---

### Post by days_of_ruin on 2008-07-20
> **mssever said:**
> My first experiment with Inkscape...

EDIT:I also noticed that your location is similar to mine. :)

:lolflag:.So you live in a development house?

---

### Post by mssever on 2008-07-20
> **days_of_ruin said:**
> So you live in a development house?
No, /dev is where devices live. /dev/sd* is a hard disk, /dev/crdom is my cd drive, /dev/null is my filing cabinet :), and /dev/chair is where I sit.

---

