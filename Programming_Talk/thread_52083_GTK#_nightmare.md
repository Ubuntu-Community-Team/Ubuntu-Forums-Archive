---
title: "GTK# nightmare"
date: 2005-07-26
forum: Programming Talk
---

### Post by lol on 2005-07-26
hi, any GTK# developer here?

I am having troubles with the ListStore.RowsReordered event. Whenever I try to catch it (with something like store.RowsReordered += new RowsReorderedHandler(OnRowsReordered)), my application crashes with the following error:

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00116> Gtk.ListStore:RowsReorderedSignalCallback (IntPtr arg0, IntPtr arg1, Gtk.TreeIter arg2, System.Int32 arg3, IntPtr gch)
in (wrapper native-to-managed) Gtk.ListStore:RowsReorderedSignalCallback (intptr,intptr,Gtk.TreeIter&,int&,intptr)

Either I do something wrong (which I doubt, I can handle the other events without any problem the same way) or there is something wrong with the current version of GTK# on Ubuntu.

So, My first question is: where does the Ubuntu version (1.9.5) comes from? According to [http://gtk-sharp.sourceforge.net/](http://gtk-sharp.sourceforge.net/) , the latest unstable version is 1.9.3.

My other question is how to compile and install GTK# (from CVS) on a Ubuntu system. All I want to do is to replace the libgtk2.0-cil package, without messing too much with the other packages... Is there an easy way to do this?

Thx.

---

