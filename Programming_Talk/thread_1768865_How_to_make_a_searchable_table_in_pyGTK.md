---
title: "How to make a searchable table in pyGTK"
date: 2011-05-27
forum: Programming Talk
---

### Post by Uchiya on 2011-05-27
Hi. I want to make a table with 1 column. It will read from a file once in a while and add new lines in that file to the table. New entries must be added at the end of the table.     Also, I want to have a text box and when I write text there it will grep the table and only the rows with that text will be shown in the table.     I'm programming with pyGTK and Glade. I think I have to use treeviews but I'm not sure.   Can you guide me on which widget I have to use? (if treeview, what model? I still don't understant most of treeviews)  Where can I get an example of this?   Thanks

---

### Post by r-senior on 2011-05-27
The tutorials on here are about the best I've found for PyGTK with Glade: 

[http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html](http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html)

From your description it sounds like you need a gtk.Treeview backed by a gtk.Liststore for the table. The text field is a gtk.Entry.

If you don't have Devhelp installed (it's in the repositories), I'd also suggest you do that. It includes the PyGTK reference manual and the documentation of the widgets includes small examples.

Also:

[http://scentric.net/tutorial/treeview-tutorial.html](http://scentric.net/tutorial/treeview-tutorial.html)

[http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm](http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm)

[http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/gtk-glade-tutorial-part-1.html)

When you have it all figured out, you can explain it to me. ;)

---

### Post by simeon87 on 2011-05-27
You have to use a gtk.TreeView with gtk.ListStore or gtk.TreeStore. You can then use [http://www.pygtk.org/docs/pygtk/class-gtktreeview.html#method-gtktreeview--set-enable-search](http://www.pygtk.org/docs/pygtk/class-gtktreeview.html#method-gtktreeview--set-enable-search) (set_enable_search) to enable searching in the table. You can also write your own search using a gtk.Entry in which the user can type text or a search pattern.

---

