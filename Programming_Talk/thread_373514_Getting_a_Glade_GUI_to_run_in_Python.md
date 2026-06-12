---
title: "Getting a Glade GUI to run in Python?"
date: 2007-03-01
forum: Programming Talk
---

### Post by TheForkOfJustice on 2007-03-01
Can someone post the minimal python scripting code that will get a Glade GUI file to run and walk me through it a bit?

---

### Post by duff on 2007-03-01
here's the barest of bare:
```
import gtk
import gtk.glade
xml = gtk.glade.XML('/usr/share/update-manager/glade/UpdateManager.glade','window_main')
window = xml.get_widget('window_main')
window.connect('destroy',gtk.main_quit)
window.show_all()
gtk.main()

```

the only main point is the XML object.  First parameter is the path, the second is the name of the widget.

---

### Post by TheForkOfJustice on 2007-03-01
Okay, that works.

Now can you help me figure out what's happening here:

```
login@system:~/lab_software$ python rungui.py
rungui.py:17: GtkWarning: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed
  xml = gtk.glade.XML('lab_software.glade','MainLabWindow')
rungui.py:17: GtkWarning: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
  xml = gtk.glade.XML('lab_software.glade','MainLabWindow')
rungui.py:21: GtkWarning: gtk_widget_get_clipboard: assertion `gtk_widget_has_screen (widget)' failed
  gtk.main()
rungui.py:21: GtkWarning: gtk_clipboard_get_owner: assertion `clipboard != NULL' failed
  gtk.main()
```Also, for some reason, the first five (or so) tabs in my GUI don't want to work.  I click on them but they refuse to show their contents or only do so once and never again.  It may be due to the amount of widgets under those tabs but I doubt it because the first tab is very simple and should be displaying if that were the case.

Can you or anyone else lend a suggestion as to why tabs refuse to behave when clicked?

EDIT

Nevermind the tabs. I figured out what was wrong.  I had the tab labels as 'Selectable' so when I clicked on them I was clicking on the text and not the tab.  Works now, but that output I mentioned above makes no sense to this newbie programmer.

---

