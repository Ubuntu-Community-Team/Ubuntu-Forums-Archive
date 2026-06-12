---
title: "Help with pyGtk - multiple windows &amp; tree view scrolling"
date: 2006-12-09
forum: Programming Talk
---

### Post by mejy on 2006-12-09
I'm attempting to make a small app with python & pygtk.  So far I'm faced with two problems:

[LIST=1]
[*]When moving treeview items, they often end up outside the currently visible area and it is unclear that the user needs to scroll up to see the item.  I need a way to programatically scroll the treeview.
[*]The app contains two windows, shown one after the other.  Each window is show with gtk.main() and destroy with gtk.main_quit().  If there's only one window, the destroy event causes the program to end.  However, if another window is shown after the first is destroyed, the program does not end on the destruction of the second one.  I have considered keeping a count of open windows and manually exiting the program when there are non left, but this seems very crude and hackish.
[/LIST]

Any help on either point much appreciated.

---

### Post by pmasiar on 2006-12-09
Looks like no pyGtk experts around. I do use python whenever I can - but for CGI and databases. Your question is rather specific: I wish you more luck at [pyGtk IRC or mailing list]("http://www.pygtk.org/feedback.html").

---

