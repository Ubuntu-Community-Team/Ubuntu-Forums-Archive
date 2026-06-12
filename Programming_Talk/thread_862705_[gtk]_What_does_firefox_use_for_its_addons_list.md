---
title: "[gtk] What does firefox use for its addons list?"
date: 2008-07-17
forum: Programming Talk
---

### Post by days_of_ruin on 2008-07-17
I am pretty sure its a some sort of treestore and that each
add has a "child" that has the extra info and buttons.But how is it 
done so that there aren't the arrows?

---

### Post by bruce89 on 2008-07-17
Firefox doesn't use GTK+. It may look much the same, but it is faked to a certain degree.

To answer your question (partially), I think you'll have to create your own subclass of GtkCellRenderer. Transmission's [TorrentCellRenderer]("http://trac.transmissionbt.com/browser/trunk/gtk/torrent-cell-renderer.c") may be of interest (apart from the coding style issues).

---

### Post by days_of_ruin on 2008-07-17
> **bruce89 said:**
> **Firefox doesn't use GTK+**. It may look much the same, but it is faked to a certain degree.

To answer your question (partially), I think you'll have to create your own subclass of GtkCellRenderer. Transmission's [TorrentCellRenderer]("http://trac.transmissionbt.com/browser/trunk/gtk/torrent-cell-renderer.c") may be of interest (apart from the coding style issues).
**link?I am talking about firefox 3 btw**

---

### Post by bruce89 on 2008-07-17
> **days_of_ruin said:**
> **link?I am talking about firefox 3 btw**

It still doesn't in 3.x. It doesn't use GTK+ natively, it's used through XUL. That's why it looks slightly alien in places (look at combo boxes on pages, they are actually old GtkOptionMenus).

---

### Post by kknd on 2008-07-17
Firefox uses GTK to render the theme, but don't use GTK for the UI (+/- like Java Swing) .

---

