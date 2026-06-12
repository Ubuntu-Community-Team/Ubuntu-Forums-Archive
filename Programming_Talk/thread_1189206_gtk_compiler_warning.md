---
title: "gtk compiler warning"
date: 2009-06-16
forum: Programming Talk
---

### Post by Woody1987 on 2009-06-16
My program might at some point display an error dialog. When my program compiles i get the following warning:

> warning: passing argument 1 of ‘gtk_message_dialog_new’ from incompatible pointer type|

Its not a problem, it still works, but i would like to get rid of it. The function is:

> void showMySqlErrorDialog(GtkWidget *window)
{
    GtkWidget *dialog;
    dialog = gtk_message_dialog_new(window, GTK_DIALOG_DESTROY_WITH_PARENT, GTK_MESSAGE_ERROR, GTK_BUTTONS_OK, "Test failed, cannot connect to database, make sure you provided the correct information");
    gtk_window_set_title(GTK_WINDOW(dialog), "Error");
    gtk_dialog_run(GTK_DIALOG(dialog));
    gtk_widget_destroy(dialog);
}

---

### Post by monraaf on 2009-06-16
Maybe you should cast argument 1 to a pointer to a window: GTK_WINDOW(window)

---

### Post by Woody1987 on 2009-06-16
> Maybe you should cast argument 1 to a pointer to a window: GTK_WINDOW(window)

Excellent work monraaf, worked like a charm.

---

### Post by dwhitney67 on 2009-06-16
> **Woody1987 said:**
> Excellent work monraaf, worked like a charm.

Yeah, if you can't solve the problem, just mask it with a cast.  :rolleyes:

---

