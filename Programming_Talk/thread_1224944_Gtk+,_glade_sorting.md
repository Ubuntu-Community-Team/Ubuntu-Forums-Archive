---
title: "Gtk+, glade sorting"
date: 2009-07-28
forum: Programming Talk
---

### Post by EricDallal on 2009-07-28
Hello,
I am making a small program with Gtk+ and glade and I have a programming question. Basically, I have a list store with multiple columns, and I would like to be able to sort by any column by clicking on that column, and to reverse the sort order by clicking a second time (kind of like the usual interface for exploring directories can be sorted by name, modification date, size, etc... by clicking on the appropriate column). Any ideas of how to do this?

There are three issues here:

1) What signal is triggered when I click on a column? Is it the "clicked" signal of the relevant GtkTreeViewColumn?
2) Is getting the sorting actually done a simple matter of changing the sort column (through gtk_tree_sortable_set_sort_column_id) and then setting the sort function through gtk_tree_sortable_set_sort_func, or is there some extra step that is necessary so that the entries are sorted in the TreeView?
3) Is the sorting method stable?

Note: I have used sorting functions in Gtk+ before, but the sorting function was constant, so I should be familiar with most of the relevant methods.

---

### Post by kknd on 2009-07-28
You can enable sorting by usinggtk_tree_view_column_set_sort_column_id ()
Just map the first column to the first model column and etc.

The sorting function isn't guaranted to be stable, in fact you can't rely on this.

---

