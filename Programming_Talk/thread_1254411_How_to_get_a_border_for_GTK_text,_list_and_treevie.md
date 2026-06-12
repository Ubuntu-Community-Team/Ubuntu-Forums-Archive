---
title: "How to get a border for GTK text, list and treeviews?"
date: 2009-08-31
forum: Programming Talk
---

### Post by resander on 2009-08-31
These three come out without borders. Here are the main steps for the textview:

GtkWidget * e = gtk_text_view_new ( ) ;
GtkTextBuffer * buf = gtk_text_view_get_buffer (GTK_TEXT_VIEW (e));
 ...
GtkWidget * scrolled_win = gtk_scrolled_window_new (NULL, NULL);
gtk_container_add (GTK_CONTAINER (scrolled_win), e); // textview to scrolled window
 ...
GtkWidget * box = gtk_fixed_new() ;  // container
gtk_container_set_border_width ( (GtkContainer *)box , 4 ) ;  <<< not working
 ...
gtk_widget_set_size_request ( scrolled_window , width, height ) ;//put scrolled window
gtk_fixed_put ( GTK_FIXED(box), scrolled_window , x , y ) ;  //at fixed pos
 ...
gtk_container_add(GTK_CONTAINER((GTK_DIALOG (dlg)->vbox)), box ); //container to dialog
gtk_widget_show_all (dlg);


I have looked at the documentation and was only able to find gtk_container_set_border_width. It didn't work. Have I used it the wrong way?
OR are there better, correct ways?

---

