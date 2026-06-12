---
title: "Accessing widgets in glade file"
date: 2010-03-06
forum: Programming Talk
---

### Post by y50a7XpWRH66IV on 2010-03-06
Hello!

Recently, I've been playing around with Glade and Anjuta to build GTK applications.

I have created a GTK+ application in Anjuta and designed a GUI using the built in Glade plugin.

I was able to compile my project and see my GUI when executing it.

I now want to access the widgets in the Glade file. For instance, I wish to dynamically modify the number of columns and rows in a GTKTable container.

I know I can use gtk_table_resize, but how do I go about getting a pointer to the table widget?

Upon some research, I found that libglade has a lookup_widget function to get a pointer to the widget. However, I am using GTKBuilder to load my glade file and was not able to find a solution to that..

Any ideas appreciated :)

---

### Post by PX9 on 2010-03-07
I have never used GtkBuilder, but [gtk-builder-get-object()]("http://library.gnome.org/devel/gtk/2.15/GtkBuilder.html#gtk-builder-get-object") seems as that you need.

---

