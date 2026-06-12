---
title: "How to get a GTK liststore selected item position as an integer?"
date: 2009-07-09
forum: Programming Talk
---

### Post by resander on 2009-07-09
My application written years ago for Windows needs an integer. It cannot use GtkTreeIters.

For example, I need index 1 to be returned for the selected item below:

```

  red
  green   <<< selected
  blue 
  ....

```


There is a function gtk_tree_selection_get_selected that returns the treeiter for currently selected item in single-select mode. In multi-select mode there is a callback function GtkTreeSelectionForeachFunc that also provides a treeiter for selected items. But how do I convert this treeiter to an integer?

A very inefficient way would be to visit all rows and check which are selected and return the integer row indexes.

I have seen a function gtk_tree_selection_get_user_data() that returns userdata for a selected row. I could store row indexes as userdata, 0 for the first row, 1 for the second and thus be able to get the integer index I want for selected rows, but I don't know how to set userdata for listrows. How?

Or are there better ways?

---

### Post by MadCow108 on 2009-07-09
edit: I somehow assumed gtkmm. but maybe its also applicable to other gtk bindings

use the get_path(iterator) method of the tree model to get the path from the iterator.
the path can return the row number as a string or an integer array with
to_string and get_indices

you could also add a hidden column with the row number and just read that the usual way. That way the number would stay the same if you allow sorting of the view

---

### Post by resander on 2009-07-10
Thanks a lot!

After some fumbling I managed to get single-select mode working (or at least it is giving the right values for the test cases I tried):

```

int getsingleselect ( GtkTreeView * tv )
   {
   GtkTreeSelection * tsel = gtk_tree_view_get_selection (tv);
   GtkTreeIter iter ;
   GtkTreeModel * tm ;
   GtkTreePath * path ;
   int * i ;
   if ( gtk_tree_selection_get_selected ( tsel , &tm , &iter ) )
      {
      path = gtk_tree_model_get_path ( tm , &iter ) ;
      i = gtk_tree_path_get_indices ( path ) ;
      return i [ 0 ] ;
      }
   return -1;
   }

```

Again many thanks

---

