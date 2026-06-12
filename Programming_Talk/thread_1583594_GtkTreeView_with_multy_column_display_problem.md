---
title: "GtkTreeView with multy column display problem"
date: 2010-09-28
forum: Programming Talk
---

### Post by phxzuo on 2010-09-28
there is a line between cloumns on ubuntu 10.04, but it doesn't apper on ubuntu 7.10 and other new linux. the attachment show this problem.
Can anyone tell me how to hide this line on ubuntu 10.04,thanks very much!

---

### Post by pbrane on 2010-09-28
In gtk+ ( C ):

```

void
gtk_tree_view_set_grid_lines(GtkTreeView *tree_view, GtkTreeViewGridLines grid_lines);

enum GtkTreeViewGridLines

typedef enum
{
  **GTK_TREE_VIEW_GRID_LINES_NONE**,
  GTK_TREE_VIEW_GRID_LINES_HORIZONTAL,
  GTK_TREE_VIEW_GRID_LINES_VERTICAL,
  GTK_TREE_VIEW_GRID_LINES_BOTH
} GtkTreeViewGridLines;

```

This for gtkmm ( C++ ):
```

void Gtk::TreeView::set_grid_lines(TreeViewGridLines grid_lines);

```

Maybe this will get rid of the column line. But it may also be theme dependent. I haven't tried this myself yet.

---

