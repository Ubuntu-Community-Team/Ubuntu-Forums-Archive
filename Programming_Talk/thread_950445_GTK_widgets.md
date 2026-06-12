---
title: "GTK widgets"
date: 2008-10-17
forum: Programming Talk
---

### Post by techmarks on 2008-10-17
How does one specify that one widget should be on top of another?

For example can I place a checkbox on a menubar?

or can I place a push button on a toolbar?

---

### Post by irrdev on 2008-10-17
From [this thread]("http://www.nabble.com/-PHP-GTK--z-index-td485856.html") on GTK+ having a "z-index":
> There's no "Z" coordinate that I've ever seen. As I see it:

1) Use show() and hide() to make sure the correct widget is displayed.

2) If you need to scrunch them together, and you need a particular one on top,
stick it on the gtkfixed after the one "underneath" in the code execution.
(this method isn't always reliable)

-Ben 

While this thread refers to php-gtk, the same applies for GTK+ and GTK#.

---

### Post by kknd on 2008-10-17
> **techmarks said:**
> How does one specify that one widget should be on top of another?

For example can I place a checkbox on a menubar?

or can I place a push button on a toolbar?

Yes, you can put almost any widget on the toolbar using GtkToolItem.

GtkToolItem is a bin Container, so you can add (almost) any widget to the GtkToolItem and them add it to the toolbar.

---

