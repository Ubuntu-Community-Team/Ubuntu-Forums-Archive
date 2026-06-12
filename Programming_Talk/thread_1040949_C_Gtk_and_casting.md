---
title: "C Gtk and casting"
date: 2009-01-16
forum: Programming Talk
---

### Post by cl333r on 2009-01-16
Hi,
I'm using C and I noticed I have to cast the widgets to the exact type to avoid warnings. Is there a way to get rid of this?

i.e. I have to cast widgets "back and forward" depending on whether the methods expect a GtkWidget or GtkWindow. Afaik GtkWindow "extends" GtkWidget so i shouldn't have to cast it to GtkWidget, the method should be aware of that. Other languages do just that and it greatly simplifies my code.

---

### Post by eye208 on 2009-01-16
> **cl333r said:**
> I'm using C and I noticed I have to cast the widgets to the exact type to avoid warnings. Is there a way to get rid of this?
You could turn off the warnings, but I wouldn't recommend it.

> Afaik GtkWindow "extends" GtkWidget so i shouldn't have to cast it to GtkWidget, the method should be aware of that.
C does not support inheritance. The compiler has no way to tell if GtkWindow is a subclass of GtkWidget.

> Other languages do just that and it greatly simplifies my code.
If you want to take full advantage of OOP, use C++ instead of C. The gtkmm library provides an OOP wrapper for GTK.

---

### Post by mike_g on 2009-01-16
I really think you want to be casting, otherwise you are more likely to end up with a hideous mess.

Gtk comes with a set of macros to cast and assert widgets. Yes, its verbose, but I would recommend using them.

---

### Post by cl333r on 2009-01-16
Thanks both,
> C does not support inheritance.The compiler has no way to tell if GtkWindow is a subclass of GtkWidget.
I think that's my issue. If I wouldn't be coming from Java I prolly wouldn't have noticed that.

---

