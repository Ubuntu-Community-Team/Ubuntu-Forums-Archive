---
title: "showing an image on selected row(GTK+)"
date: 2006-03-03
forum: Programming Talk
---

### Post by rupert on 2006-03-03
I am trying to create a programm where I have a tree_view and can selected differentt rows. when i selectr a row a picture should be displayed with the rowname.png (for now).
so how can I do that?
I tried this one, but I dont exactly cant find out how to create a function that gets the name and displays then the picture.

```

void bild_aktualisieren(gchar name)
{
  
  gchar picname;
  /* neuen Pixbuf ins Bild einschreiben und dann
	 freigeben */
 picname = sprintf("%s.png", name);
  return shot =  g_object_new(GTK_TYPE_IMAGE,"file", "picname", NULL);	
 // g_object_set(shot, "pixbuf", neuer_pixbuf, NULL);
  //g_object_unref(neuer_pixbuf);
}

void sagwas(GtkTreeSelection *auswahl, gpointer daten){

GtkTreeIter iter;
GtkTreeModel *model = NULL;

  if(gtk_tree_selection_get_selected(auswahl, &model, &iter))
  {
       gchar *name;
       gtk_tree_model_get(model, &iter, 1,  &name, -1); /*immer mit -1 am Ende*/
       g_print("Hallo %s\n",name);
  		bild_aktualisieren(name);
       g_free(name);
  }
}
------...---
this is how I call a single picture
 shot =  g_object_new(GTK_TYPE_IMAGE,"file", "bla2.png", NULL);
  
  gtk_widget_show(shot);
  gtk_fixed_put (GTK_FIXED (fixed1), shot, 24, 16);
  gtk_widget_set_size_request (shot, 376, 328);

```
its called by this
g_signal_connect(G_OBJECT(auswahl), "changed",G_CALLBACK(sagwas), NULL);

maybe someone can link me to an example for this

---

