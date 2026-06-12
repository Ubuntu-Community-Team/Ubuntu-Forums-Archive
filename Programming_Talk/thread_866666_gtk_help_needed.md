---
title: "gtk help needed"
date: 2008-07-22
forum: Programming Talk
---

### Post by dexter.deepak on 2008-07-22
i am not a very experienced programmer, so pardon me if this question sounds too stupid, but i need to know whats going on here.
this is the code snippet:
```
here is a snippet of the code i went through (from http://library.gnome.org/devel/gtk-tutorial/stable/x442.html):

              button=gtk_button_new_with_label("button1");
	g_signal_connect(G_OBJECT(button),"clicked",G_CALLBACK(callback),(gpointer)"button1");
	gtk_table_attach_defaults(GTK_TABLE(table),button,0,1,0,1);
	gtk_widget_show(button);
	button=gtk_button_new_with_label("button2");
	g_signal_connect(G_OBJECT(button),"clicked",G_CALLBACK(callback),(gpointer)"button2");
	gtk_widget_show(button);
```

i cant understand, why we have the same name "button" for two different buttons; this should create problem as button is a pointer itself and so changing it should change the widget created, and not the copy of the widget.how is this happening ?

is it just because, we are attaching and showing the button to the box, before creating a new button ?
can we create a lot of buttons with same name and attach and show them at the end of our program ?

---

### Post by ad_267 on 2008-07-22
I'm not very experienced either, but I think the way gtk works, once you have "shown" the button, the button pointer is no longer required and so you can free it, or as in this example you can point it to a new button.

---

### Post by dexter.deepak on 2008-07-22
you mean to say ,that if we want to use the same name, then its a requisite to attach & show the button one by one, and not altogether ??

---

