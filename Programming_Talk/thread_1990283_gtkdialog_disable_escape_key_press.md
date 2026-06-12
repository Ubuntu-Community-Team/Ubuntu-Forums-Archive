---
title: "gtkdialog disable escape key press ?"
date: 2012-05-29
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-29
Hello friends,

I had written a code for the dialog box to be displayed to ask any question to the user, with the help of gtk. Have a look in the code below:

```
gboolean
ask_question (GtkWidget *parent, const gchar *question)
{
    GtkWidget *dialog;
    gboolean ret = false;
    GdkColor bg_color_dialog;

    gdk_color_parse ("light yellow", &bg_color_dialog);

    dialog = gtk_message_dialog_new_with_markup (NULL, GTK_DIALOG_MODAL | GTK_DIALOG_DESTROY_WITH_PARENT,
            GTK_MESSAGE_QUESTION,
            GTK_BUTTONS_YES_NO,
            "%s", question
     );
                                                                                            
    gtk_window_set_title (GTK_WINDOW (dialog), GET_PKG_LONG_NAME);
    gtk_window_set_position (GTK_WINDOW (dialog), GTK_WIN_POS_CENTER_ON_PARENT);
    gtk_window_set_transient_for (GTK_WINDOW (dialog), GTK_WINDOW (parent));
    gtk_window_set_type_hint (GTK_WINDOW (dialog), GDK_WINDOW_TYPE_HINT_SPLASHSCREEN);

    gtk_widget_modify_bg (GTK_WIDGET (dialog), GTK_STATE_NORMAL, &bg_color_dialog);
    
    if (gtk_dialog_run (GTK_DIALOG (dialog)) == GTK_RESPONSE_NO)
        ret = false;
    else
        ret = true;
    
    gtk_widget_destroy (dialog);
    
    return ret;
}
```The dialog box is displaying correctly and working correctly except one problem. When I press the ESC key when the dialog box is open, the default goes to GTK_RESPONSE_YES which causes the resulted operation to be performed, which I don't want. In other words I want to disable the ESC key press.
Even I tried with this signal but no success:
```
gboolean
dialog_key_press_event (GtkWidget *widget, GdkEventKey *event, gpointer data)
{
    if (event->keyval == GDK_KEY_Escape)
        return true;
    else
        return false;
}
```
How can I do that?

---

### Post by etdsbastar on 2012-05-29
Is there anyone to help me please.

---

