---
title: "focus_in_event problem GTK+"
date: 2009-07-23
forum: Programming Talk
---

### Post by pacofvf on 2009-07-23
Sorry for bad English.... I cant make a row(tree_view) to grab focus in a scrolled window... i have tried many ways...here is some of my code:
```

model=create_and_fill_model(13);
view =  g_object_new(GTK_TYPE_TREE_VIEW, "model", model, "rules-hint", TRUE, "enable-search", TRUE, "search-column", 0, NULL);
text_renderer = gtk_cell_renderer_text_new();  
col = gtk_tree_view_column_new_with_attributes("foo", text_renderer, "text", 0, NULL);
gtk_tree_view_append_column(view, col);
/*more cols
.
.
*/
gtk_tree_view_append_column(view, col);
select = gtk_tree_view_get_selection (view);
gtk_tree_selection_set_mode (select, GTK_SELECTION_SINGLE);
g_signal_connect (G_OBJECT (select), "changed", G_CALLBACK (tree_selection_changed_cb2), NULL);
gtk_scrolled_window_add_with_viewport (GTK_SCROLLED_WINDOW(scrolledwindow), GTK_WIDGET(view));
programa->view6=scrolledwindow;
//g_signal_connect (G_OBJECT (select), "focus_in_event", G_CALLBACK (focus_in_callback), (gpointer) gtk_scrolled_window_get_vadjustment(GTK_SCROLLED_WINDOW(scrolledwindow)) ); //this is for method 1
g_signal_connect (G_OBJECT (view), "focus_in_event", G_CALLBACK (focus_in_callback), (gpointer)select); //this for method 2

//then somewhere else
void focus_in_callback (GtkWidget *widget, GdkEvent *event, gpointer data){
 /* GtkWidget *adj=(GtkWidget *)data; //for method 1
//  GtkAllocation alloc=gtk_widget_get_allocation(widget); //older versions of GTK+
  GtkAllocation alloc=widget->allocation;
  gtk_adjustment_set_value(GTK_ADJUSTMENT(adj),alloc.y);
  gtk_scrolled_window_set_vadjustment(GTK_SCROLLED_WINDOW(programa->view6),GTK_ADJUSTMENT(adj));*/
  //for method 2
  gtk_widget_grab_focus(GTK_WIDGET(data));
}


```

---

