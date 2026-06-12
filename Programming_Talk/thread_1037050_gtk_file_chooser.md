---
title: "gtk file chooser"
date: 2009-01-11
forum: Programming Talk
---

### Post by Woody1987 on 2009-01-11
Im writing a small program which at some stage requires the user to open a file using a GTK_FILE_CHOOSER dialog. I have this part working. what im having trouble with is being able to set a filter on what they can choose. For example only choose mp3 files. I've had a look at GTK_FILE_FILTER but didnt get very far. Any help appreciated. Oh and im writing it in C.

---

### Post by SledgeHammer_999 on 2009-01-11
Use gtk_file_chooser_add_filter() to add a filter to the dialog -->[http://library.gnome.org/devel/gtk/stable/GtkFileChooser.html#gtk-file-chooser-add-filter](http://library.gnome.org/devel/gtk/stable/GtkFileChooser.html#gtk-file-chooser-add-filter)

An exapmle filter for an mp3 is:
```

GtkFileFilter * filter =  gtk_file_filter_new();
gtk_file_filter_set_name(filter, "Mp3 files");
gtk_file_filter_add_pattern(filter, "*.mp3");

```
or
```

GtkFileFilter * filter =  gtk_file_filter_new();
gtk_file_filter_set_name(filter, "Mp3 files");
gtk_file_filter_add_mime_type(filter, "audio/mpeg");

```
or
```

GtkFileFilter * filter =  gtk_file_filter_new();
gtk_file_filter_set_name(filter, "Mp3 files");
gtk_file_filter_add_mime_type(filter, "audio/mpeg");
gtk_file_filter_add_pattern(filter, "*.mp3");

```

For more info on file filter-->[http://library.gnome.org/devel/gtk/stable/gtk-gtkfilefilter.html#GtkFileFilter](http://library.gnome.org/devel/gtk/stable/gtk-gtkfilefilter.html#GtkFileFilter)

---

### Post by Woody1987 on 2009-01-11
thankyou, worked like a treat

---

