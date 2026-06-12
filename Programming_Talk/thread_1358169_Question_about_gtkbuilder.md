---
title: "Question about gtkbuilder"
date: 2009-12-18
forum: Programming Talk
---

### Post by j7%&lt;RmUg on 2009-12-18
Hey,

i dont really have a big problem here, but i have just converted my pygtk app to gtkbuilder from libglade and i noticed in the pygtk docs that one thing lacking is proper support for drop down boxes.

What i want to know is, is there a workaround for this? or another way of using gtkbuilder and dropdown boxes together?

I really would like to use dropdown boxes in my app still.

Thanks in advance.

---

### Post by j7%&lt;RmUg on 2009-12-19
BUMP, i have done some more research but still cannot find much information reffering to this.

---

### Post by diesch on 2009-12-19
The only problem I know about is that you can't specify item for a gtk.ComboBox in Glade if you want to use gtk.Builder. So you either have to use a gtk.ListStore to populate the ComboBox or use some dummy widget in Glade and replace it in yourt code with a ComboBox created by gtk.combo_box_new_text()

---

