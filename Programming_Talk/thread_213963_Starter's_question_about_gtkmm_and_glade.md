---
title: "Starter's question about gtkmm and glade"
date: 2006-07-12
forum: Programming Talk
---

### Post by benjaminzsj on 2006-07-12
I've just started Gtk programming using gtkmm and glade.
As I learned, I should create a Gtk::Window class and instantiate it then put it in Gtk::Main::run() function so that I can run the app with GUI. But how can that be if all my widgets are in the xml file and nothing to do with my code? I mean all my widgets are obtained using get_widget() function and shouldn't be included in the former Window class. 
There's a gtk_widget_show() and gtk_main() in a C and Gtk tutorial, is that what I could do in my code?

---

