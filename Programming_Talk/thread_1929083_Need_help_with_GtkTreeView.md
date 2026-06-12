---
title: "Need help with GtkTreeView"
date: 2012-02-21
forum: Programming Talk
---

### Post by Petrolea on 2012-02-21
Hi everyone!

I'm making a cinema program, which is showing movies names and the dates when they're playing. 

When I select a certain row in GtkTreeView everything works fine, I can get the value out of it, but what I want to do is to select a child row and then get the value of its parent too (when I select a date I also want to select movie name).

How could I do this? Any ideas?

This is the code for getting the value out of row that is selected:
[PHP]
void row_act(GtkTreeView *treeview, GtkTreePath *treepath, GtkTreeViewColumn *column, void* data)
{
	GtkTreeSelection *selection;
	GtkTreeModel *model;
	GtkTreeIter iter;
	gchar *value;

	selection = gtk_tree_view_get_selection(treeview);
	gtk_tree_selection_get_selected(selection, &model, &iter);
	gtk_tree_model_get(model, &iter, 0, &value, -1);
	g_print("Value: %s\n", value);
	g_free(value);
}
[/PHP]

Thanks in advance!

---

