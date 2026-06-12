---
title: "GTK Widget Size (actual size, not requested size)"
date: 2009-04-18
forum: Programming Talk
---

### Post by sekinto on 2009-04-18
What method in Python (PyGTK) gets a GTK Widget's actual size, as in the ammount of space it is currently taking up (not the size it is requesting).

---

### Post by sekinto on 2009-04-18
Okay, I think I found the answer:
mywidget.allocation()
But when I do:
mywidget.allocation()
OR
mywidget.allocation().width
I get:
TypeError: 'gtk.gdk.Rectangle' object is not callable

---

### Post by days_of_ruin on 2009-04-18
> **sekinto said:**
> Okay, I think I found the answer:
mywidget.allocation()
But when I do:
mywidget.allocation()
OR
mywidget.allocation().width
I get:
TypeError: 'gtk.gdk.Rectangle' object is not callable

Do either:
```
mywidget.get_allocation().width
```
or ```
mywidget.allocation.width
```

mywidget.allocation is an attribute and mywidget.get_allocation is a function.

---

### Post by jonny on 2009-04-18
I've used this in some of my code:
```
x_size, y_size = mywidget.window.get_size()

```
I've only used it in connection with Cairo drawing widgets, but I think it'll work for generic widgets.  And, like you, I found it a very difficult question to answer from the official documentation.

---

### Post by sekinto on 2009-04-18
Ah, thank you.

---

