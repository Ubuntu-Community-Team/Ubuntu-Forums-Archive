---
title: "Closing gtk filechoosers"
date: 2007-07-09
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-07-09
Hi all,

What is the proper way to close GtkFileChoosers? (I'm using glade and C)

Using gtk_widget_destroy(widget) throws an assertion error saying that GTK_IS_WIDGET failed.

Thanks

---

### Post by duff on 2007-07-09
how about g_object_unref?

---

### Post by AlexThomson_NZ on 2007-07-09
Yeah I tried that, but that caused more errors.

I ended up getting around it, having another function especially for closing the filechooser by the cancel button.  It works fine with no errors or warnings, but seems like a bit of a hack, would have thought there was a more elegant way to do such a common thing...

```

void close_button_clicked(GtkWidget *widget, gpointer user_data) {
	GtkFileChooser *fcd = GTK_FILE_CHOOSER(glade_xml_get_widget (filechooserdialog, "filechooserdialog1"));
	close_filechooser(GTK_WIDGET(fcd),NULL);
}

```

---

