---
title: "Is this possible with Gtkmm?"
date: 2010-02-10
forum: Programming Talk
---

### Post by kahumba on 2010-02-10
Hi,
I have a Java app I'd like to migrate to C++/gtkmm.
It uses large JTables.

In Java to make the app snappier I don't fill in the JTable, I only set the JTable row count to the number of objects to display + using a custom JTable cell renderer, so that I don't actually have to fill in the whole table before showing up the results (several thousand rows). I just set its size and the custom renderer fills in the data as the user scrolls (kind of "if the user doesn't see the trees falling they don't fall" approach).

In C++/gtkmm using a TreeView I don't  have a clue how to do it. So before showing the results I actually fill in each of row of the TreeView. Because of this the app doesn't seem "lightning fast" as it is in Java.

Did anyone do something like that in Gtkmm?

PS: this post has nothing to do with premature optimization

---

### Post by pbrane on 2010-02-10
I have not tried what you want to do in Gtkmm, however there are cellrenders in gtkmm that you *should* be able to use to do the same thing. Look at the Gtk::CellRenderer class. You should be able to tell if a cell ( or row ) is visible or not.

---

### Post by kahumba on 2010-02-10
Thanks, I saw there's a CellRenderer but I thought it will take me a long time to figure out how to make it all work correctly so I hoped someone did this already and had some working code.

---

