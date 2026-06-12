---
title: "Gio::Icon load image"
date: 2013-02-11
forum: Programming Talk
---

### Post by bird1500 on 2013-02-11
Hi,
1) there are gio/gtk classes that return a Gio::Icon (like Gio::Volume::get_icon()) - how does one actually load the image the icon refers to?
2) How do I determine what the Gio::Icon really is (FileIcon/ThemedIcon)? I'm asking cause the to_string() method says:

> 
Generates a textual representation of *icon* that can be used for serialization such as when passing *icon* to a different process or saving it to persistent storage. 
 Use g_icon_new_for_string() to get *icon* back from the returned string.
 The encoding of the returned string is proprietary to Icon except in the following two cases
 
[LIST]
[*]If *icon* is a FileIcon, the returned string is a native path (such as /path/to/my icon.png) without escaping if the File for *icon* is a native file. If the file is not native, the returned string is the result of g_file_get_uri() (such as sftp://path/to/my%20icon.png).
[*]If *icon* is a ThemedIcon with exactly one name, the encoding is simply the name (such as network-server).
[/LIST]



---

### Post by SledgeHammer_999 on 2013-02-11
How about:

1. [http://developer.gnome.org/gtkmm/3.2/classGtk_1_1Image.html#a6420311c6012c9515ef3071387499f1f](http://developer.gnome.org/gtkmm/3.2/classGtk_1_1Image.html#a6420311c6012c9515ef3071387499f1f)
2. [http://developer.gnome.org/gtk3/stable/GtkImage.html#gtk-image-new-from-gicon](http://developer.gnome.org/gtk3/stable/GtkImage.html#gtk-image-new-from-gicon)

?

---

### Post by bird1500 on 2013-02-11
Wow, thanks.
set (const [Glib::RefPtr]("http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1RefPtr.html")< const [Gio::Icon]("http://library.gnome.org/devel/glibmm/unstable/classGio_1_1Icon.html") >& icon, IconSize [size]("http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/a00301.html#a7d6d850b7c581f119ba12205c6037635"))
is cool, I missed that one, I focused too much on Gdk::Pixbuf.

However,  the 2nd link won't work in Gtkmm since a constructor Gtk::Image(Gio::Icon) is not exposed apparently, but I don't need it since the solution in the 1st link is good enough.

Problem solved.

I'm just curious, according to the quotation from 1st post how does one determine if, apparently, a Gio::Icon is/could be actually a ThemedIcon or anything else, using Gtkmm (C++ not C).

---

### Post by SledgeHammer_999 on 2013-02-11
I provided the second link because the description of the first reference it. When using gtkmm you have to go back to the gtk docs because the gtkmm ones arent so complete.

As for the other question I have no idea.

---

### Post by SledgeHammer_999 on 2013-02-11
Actually I have an idea. Use dynamic_cast on ::icon and if it converts to fileicon or themedicon (or it is actually a gicon)

---

