---
title: "gtk+ gcallback multiple args"
date: 2012-04-23
forum: Programming Talk
---

### Post by chukchuck on 2012-04-23
I have this callback:
```
void b_clicked (GtkButton *c_button, GtkWidget *h_name, GtkWidget *u_name){
	g_print("Hostname: %s\nUsername: %s\n", gtk_entry_get_text(GTK_ENTRY(h_name)), gtk_entry_get_text(GTK_ENTRY(u_name)));
}
```
and i want to pass 2 args to its (h_name and u_name).
I've tried with:
```
g_signal_connect (c_button, "clicked", G_CALLBACK (b_clicked), h_name);
g_signal_connect (c_button, "clicked", G_CALLBACK (b_clicked), u_name);
```
and also with
```
g_signal_connect (c_button, "clicked", G_CALLBACK (b_clicked), h_name, u_name);
```
but i cannot get it works :(

PS: i'm developing with GTK+ v3.4.0 in Ubuntu 12.04!

---

