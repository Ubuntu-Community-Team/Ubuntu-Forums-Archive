---
title: "Gtk/Pango help"
date: 2006-11-10
forum: Programming Talk
---

### Post by zootreeves on 2006-11-10
Does anyone know what I'm doing wrong here. I trying to create a simple tree view with text in each colum.


void plugins_loop(gchar * dir) {

  GtkTreeIter    *iter;
  gchar string[100];
  strcpy(string, "my string");


  /* Append a row and fill in some data */
  gtk_list_store_append (store, iter);
  gtk_list_store_set (store, iter,
                      COL_NAME, string,
                      -1);
}

It compiles fine without warning, but when i run it I get.

Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text() and ??Hx?@@ is displayed in the colums

I can't figure it out? Is it something wrong with my setup?

---

