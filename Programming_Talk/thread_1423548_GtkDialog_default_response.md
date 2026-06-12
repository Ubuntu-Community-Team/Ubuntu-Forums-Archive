---
title: "GtkDialog default response"
date: 2010-03-06
forum: Programming Talk
---

### Post by Milliways on 2010-03-06
I am trying to create a dialog box which allows a user to select a response by pressing "Enter" (like the Gnome Commander Copy dialog)

Unfortunately the code below does not recognise "Enter" - it is necessary to click on the OK button.
("Esc" does cancel the dialog).

Can anyone suggest how to change this behaviour?

```

gchar * copy_dialog()
{
    GtkWidget *dialog;
    GtkWidget *entry;
    GtkWidget *content;
    gchar *result = NULL;
    GtkWidget	*window = NULL;

    dialog = gtk_dialog_new_with_buttons("File selection",
                                GTK_WINDOW(window),
				GTK_DIALOG_DESTROY_WITH_PARENT,
				GTK_STOCK_CANCEL,
				GTK_RESPONSE_REJECT,
				GTK_STOCK_OK,
				GTK_RESPONSE_ACCEPT,
				NULL);

    gtk_dialog_set_has_separator(GTK_DIALOG(dialog), FALSE);
    content = gtk_dialog_get_content_area(GTK_DIALOG(dialog));

    entry = gtk_combo_box_entry_new_text();
    gtk_combo_box_append_text(GTK_COMBO_BOX(entry), "test line 1");
    gtk_combo_box_append_text(GTK_COMBO_BOX(entry), "test line 2");
    gtk_combo_box_set_active(GTK_COMBO_BOX(entry), 0);

    gtk_box_pack_start(GTK_BOX(content), gtk_label_new("Copy file"), FALSE, FALSE, 1);
    gtk_box_pack_start(GTK_BOX(content), entry, FALSE, FALSE, 1);
    gtk_dialog_set_default_response(GTK_DIALOG(dialog), GTK_RESPONSE_ACCEPT);
    gtk_widget_show_all(dialog);

    if (gtk_dialog_run(GTK_DIALOG(dialog)) == GTK_RESPONSE_ACCEPT)
      {
	result = gtk_combo_box_get_active_text(GTK_COMBO_BOX(entry));
      }
    gtk_widget_destroy(dialog);
    return result;
}

```

---

### Post by Milliways on 2010-04-01
[QUOTE=Milliways;8927544]I am trying to create a dialog box which allows a user to select a response by pressing "Enter" (like the Gnome Commander Copy dialog)

I figured out how to do this, by connecting to the activate signal of the GtkEntry

```

[COLOR="Red"]static void enter_callback(GtkWidget *widget, GtkWidget *dialog)
{
    g_signal_emit_by_name(G_OBJECT(dialog), "response", GTK_RESPONSE_ACCEPT);
}
[/COLOR]
gchar * copy_dialog(GtkWidget	*window)
{
    GtkWidget *dialog;
    GtkWidget *entry;
    GtkWidget *content;
    gchar *result = NULL;
    guint event_handler_id;

    dialog = gtk_dialog_new_with_buttons("File selection",
                                         GTK_WINDOW(window),
                                         //~ GTK_DIALOG_MODAL | GTK_DIALOG_DESTROY_WITH_PARENT,
                                         GTK_DIALOG_DESTROY_WITH_PARENT,
                                         GTK_STOCK_CANCEL,
                                         GTK_RESPONSE_REJECT,
                                         GTK_STOCK_OK,
                                         GTK_RESPONSE_ACCEPT,
                                         NULL);
    gtk_dialog_set_has_separator(GTK_DIALOG(dialog), FALSE);
    content = gtk_dialog_get_content_area(GTK_DIALOG(dialog));

    entry = gtk_combo_box_entry_new_text();
    gtk_combo_box_append_text(GTK_COMBO_BOX(entry), "test line 1");
    gtk_combo_box_append_text(GTK_COMBO_BOX(entry), "test line 2");
    gtk_combo_box_set_active(GTK_COMBO_BOX(entry), 0);

[COLOR="Red"]    event_handler_id = g_signal_connect(G_OBJECT(gtk_bin_get_child(GTK_BIN(entry))), "activate",
                     G_CALLBACK(enter_callback),
                     (gpointer) dialog);
[/COLOR]
    gtk_box_pack_start(GTK_BOX(content), gtk_label_new("Copy file"), FALSE, FALSE, 1);
    gtk_box_pack_start(GTK_BOX(content), entry, FALSE, FALSE, 1);
    gtk_dialog_set_default_response(GTK_DIALOG(dialog), GTK_RESPONSE_ACCEPT);
    gtk_widget_show_all(dialog);

    if (gtk_dialog_run(GTK_DIALOG(dialog)) == GTK_RESPONSE_ACCEPT)
    {
        result = gtk_combo_box_get_active_text(GTK_COMBO_BOX(entry));
    }
    g_signal_handler_disconnect(G_OBJECT(gtk_bin_get_child(GTK_BIN(entry))), event_handler_id);
    gtk_widget_destroy(dialog);
    return result;
}
```

---

### Post by peterius on 2012-01-12
```

gtk_entry_set_activates_default(entry, TRUE);

gtk_dialog_set_default_response(GTK_DIALOG(dialog), GTK_RESPONSE_ACCEPT);

```

---

