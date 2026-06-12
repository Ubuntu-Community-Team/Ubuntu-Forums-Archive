---
title: "Cloning a gtk widget"
date: 2009-06-09
forum: Programming Talk
---

### Post by Origin415 on 2009-06-09
Is it possible to have a single widget object appear in multiple places in an interface?

For example, to have a label object and put it in several places in the gui, and be able to call gtk_label_set_text() once to update them all?

If not, is there a better way to get this behavior than to simply iterate over all the labels I want to update?

Thanks

---

### Post by crdlb on 2009-06-09
No, a widget can only have one parent. I don't see anything particularly horrible about needing to set multiple labels, but you could create an object that has a property containing the mutable portion of text. Then you would connect to the "notify::propertyname" signal for each label. You could also add a new signal for it, but GObject property notification is often sufficient.

---

### Post by Origin415 on 2009-06-10
Thats quite a bit over my head, so I just put in an iterator. :/

Right now I only needed it for labels, so just looping over them all is fine, but my question was more directed at more complex widgets that I might want this functionality for in the future. Oh well.

Thanks.

---

