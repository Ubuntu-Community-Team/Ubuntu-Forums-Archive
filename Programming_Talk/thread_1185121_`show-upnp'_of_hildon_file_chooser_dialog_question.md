---
title: "`show-upnp' of hildon file chooser dialog question..."
date: 2009-06-11
forum: Programming Talk
---

### Post by prosteven2 on 2009-06-11
hello.

**code firstly:**
[COLOR=Green]///////////////////////[/COLOR]
GtkWidget* dlg = hildon_file_chooser_dialog_new_with_properties( GTK_WINDOW(widget), "action", GTK_FILE_CHOOSER_ACTION_SELECT_FOLDER, "title", "Open folder", NULL );
  
gtk_widget_show_all( dlg );
gint response = gtk_dialog_run( (GtkDialog*)dlg );
[COLOR=Green]///////////////////////[/COLOR]

**result:**
[IMG]http://1813.img.pp.sohu.com.cn/images/2009/6/11/19/12/1227b55799eg213.jpg[/IMG]

By clicking "New" and try to make a new sub-folder,the X terminal has the following outputs:

[COLOR=Blue] GLIB WARNING ** GLib-GObject - IA__g_object_new_valist: object class `HildonFileChooserDialog' has no property named `show-upnp'[/COLOR]


[COLOR=DarkOrange]What does this mean?what's "show-upnp"?[/COLOR]

---

### Post by prosteven2 on 2009-06-11
...operation faild...once again,i got the output:

GLIB WARNING ** GLib-GObject - gsignal.c:1541: signal "voldev_mounted" already exists in the `HildonFileSystemModel' class ancestry

---

