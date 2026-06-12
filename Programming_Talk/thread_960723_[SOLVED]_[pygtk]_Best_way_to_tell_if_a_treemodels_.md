---
title: "[SOLVED] [pygtk] Best way to tell if a treemodels rows have been reordered?"
date: 2008-10-27
forum: Programming Talk
---

### Post by days_of_ruin on 2008-10-27
Like when the you drag the treeview rows to change their order.
What I want to know is how to call a function when that happens.
I have googled it and got some workarounds but there aren't very simple
and I am hoping some one here know a good way.

---

### Post by days_of_ruin on 2008-10-27
Never mind I figured it out.
I did this: ```
treeview.connect("drag-end",func)
```

This will call "func" whenever the user finishes reordering treeview rows.


:guitar::guitar::guitar:

---

