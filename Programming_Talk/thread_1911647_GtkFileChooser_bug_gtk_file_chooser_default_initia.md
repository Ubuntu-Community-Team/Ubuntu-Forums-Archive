---
title: "GtkFileChooser bug: gtk_file_chooser_default_initial_focus"
date: 2012-01-19
forum: Programming Talk
---

### Post by tonemgub on 2012-01-19
Hi,

I am developing an application using c, glade and gtkbuilder and I noticed a bug, probably related to gtk. When I open my file chooser, and click on one of the "places" (left column of the file chooser), I get the following warning:

```
(gnac:16155): Gtk-CRITICAL **: _gtk_file_chooser_entry_set_file_part: assertion `GTK_IS_FILE_CHOOSER_ENTRY (chooser_entry)' failed
```

This warning is annoying, but does not disturb the execution of the program. 
The problem comes when I try to open the file chooser a second time (after getting the previous warning). Then, the execution of the program is aborted with the following error:

```
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.24.6/gtk/gtkfilechooserdefault.c:8751:gtk_file_chooser_default_initial_focus: assertion failed: (widget != NULL)
Aborted
```

I am using ubuntu oneiric and gtk version is 2.24.6. I googled the problem and it seems it is supposed to be fixed (obviously it is not). Apparently geany had the same problem and found a workaround.

Does anybody know how to fix this issue (or what workaround was used by geany)?

Thanks for your help.

---

### Post by tonemgub on 2012-01-19
I tried compiling my application against gtk3 to see if this could solve the problem, but I cannot run my application as I get the following error:

```
Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
```

Any idea how to solve that and locate the gtk2 symbols?

Thanks.

---

