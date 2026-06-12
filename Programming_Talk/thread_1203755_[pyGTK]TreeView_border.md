---
title: "[pyGTK]TreeView border"
date: 2009-07-03
forum: Programming Talk
---

### Post by dom96 on 2009-07-03
hello how can i set a TreeViews border and color in pyGTK ?

---

### Post by days_of_ruin on 2009-07-04
AFAIK TreeViews don't actually have an edge. You could stick it inside
a ScrolledWindow or Viewport and then set the border on them.

---

### Post by dom96 on 2009-07-04
hi and thanks for the reply, i already have it in a scrolled window, how can i set the border of a scrolled window then ?

---

### Post by days_of_ruin on 2009-07-04
[http://pygtk.org/docs/pygtk/class-gtkscrolledwindow.html#method-gtkscrolledwindow--set-shadow-type]("http://pygtk.org/docs/pygtk/class-gtkscrolledwindow.html#method-gtkscrolledwindow--set-shadow-type")

Not sure how to change the color though.

---

