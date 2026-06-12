---
title: "GtkFileChooserDialog Error"
date: 2008-10-09
forum: Programming Talk
---

### Post by arloth on 2008-10-09
I've been working on learning GTK+, and have been making very good progress, but have run into a rather annoying issue with the File Chooser Dialog.  

The goal in this case, was to keep the user in a specific folder. Depending on what version of GTK+ you're using you get a side pane with a folder selection, folder navigation buttons on the top, and a manual text entry widget.  As best of knowledge the top buttons and text entry widgets aren't able to be hidden. 

So there is a bit of code bound to the current_folder_changed event, with some extra stuff in there, but this is the meat of it really: 

```

pathlen = strlen(widgets->dirtostay);
if(strncmp(widgets->dirtostay, the_path , pathlen) != 0) {
  fprintf(stderr, "%s - %s and %s don't match.\n", __func__, widgets->dirtostay, the_path);
  gtk_file_chooser_set_current_folder(GTK_FILE_CHOOSER(dialog), widgets->dirtostay);
}

```

When the top navigation buttons are clicked, I get a wonderful error: 
```
Gtk-CRITICAL **: gtk_file_folder_unix_get_info: assertion `strcmp (dirname, folder_unix->filename) == 0' failed
```
Now this doesn't crash it in ubuntu with libgtk-x11-2.0.so.0.1200.9. However, compiling in Scientific Linux 5.1, with libgtk-x11-2.0.so.0.1000.4 clicking the root folder icon outright segfaults it. :cry:  This code works great in SL 4.1 with the ancient libgtk-x11-2.0.so.0.400.13 but in that case the top buttons don't allow navigation back up the directory tree.

Is there something I'm doing wrong to prevent this? Has somebody else managed to make functioning code that constrains the user to a set directory?

Valgrind doesn't throw any errors on this in ubuntu, but in SL 5.1, it spits lovely things out on the segfault. In case it's of any use to anybody I'll post it as well.
```
==8220== Invalid read of size 1
==8220==    at 0x400630E: strcmp (mc_replace_strmem.c:341)
==8220==    by 0x20E3A0B: (within /usr/lib/libgtk-x11-2.0.so.0.1000.4)
==8220==    by 0x20C8150: (within /usr/lib/libgtk-x11-2.0.so.0.1000.4)
==8220==    by 0x2266D3F: (within /usr/lib/libgtk-x11-2.0.so.0.1000.4)
==8220==    by 0x2266E07: (within /usr/lib/libgtk-x11-2.0.so.0.1000.4)
==8220==    by 0x7A935E0: (within /lib/libglib-2.0.so.0.1200.3)
==8220==    by 0x7A95341: g_main_context_dispatch (in /lib/libglib-2.0.so.0.1200.3)
==8220==    by 0x7A9831E: (within /lib/libglib-2.0.so.0.1200.3)
==8220==    by 0x7A986C8: g_main_loop_run (in /lib/libglib-2.0.so.0.1200.3)
==8220==    by 0x20AB9EA: gtk_dialog_run (in /usr/lib/libgtk-x11-2.0.so.0.1000.4)
==8220==    by 0x80492FF: button_clicked (savefile.c:85)
==8220==    by 0x7B20258: g_cclosure_marshal_VOID__VOID (in /lib/libgobject-2.0.so.0.1200.3)
==8220==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==8220==
==8220== Process terminating with default action of signal 11 (SIGSEGV)
==8220==  Access not within mapped region at address 0x0


```

---

