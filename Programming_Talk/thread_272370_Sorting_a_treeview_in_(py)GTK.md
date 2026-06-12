---
title: "Sorting a treeview in (py)GTK"
date: 2006-10-06
forum: Programming Talk
---

### Post by kripkenstein on 2006-10-06
I can't figure something out in pygtk (it's probably the same issue when using GTK in C).

I have a treeview. Now, if the user clicks a column's header, it will sort according to that column. What I want to do, is to sort by one of the columns automatically, without user input. Basically, I want the treeview to start out sorted; later the user can resort, that's ok.

I can't figure out how to sort the treeview in my code. There are classes that deal with sorting treeMODELs; but I don't want to sort the data, I just want to sort the view. Basically, I want to simulate a user clicking a certain header :)

Any help is appreciated...

---

### Post by duff on 2006-10-08
> **kripkenstein said:**
> Basically, I want to simulate a user clicking a certain header :)


Then do that.  [emit]("http://pygtk.org/docs/pygobject/class-gobject.html#method-gobject--emit") the [clicked]("http://pygtk.org/docs/pygtk/class-gtktreeviewcolumn.html#signal-gtktreeviewcolumn--clicked") signal to the column you want initially sorted.

---

### Post by kripkenstein on 2006-10-08
> **duff said:**
> Then do that.  [emit]("http://pygtk.org/docs/pygobject/class-gobject.html#method-gobject--emit") the [clicked]("http://pygtk.org/docs/pygtk/class-gtktreeviewcolumn.html#signal-gtktreeviewcolumn--clicked") signal to the column you want initially sorted.

Excellent suggestion, that worked perfectly.

Thanks!

---

