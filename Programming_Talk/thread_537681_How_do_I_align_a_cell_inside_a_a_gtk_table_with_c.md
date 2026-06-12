---
title: "How do I align a cell inside a a gtk table with c?"
date: 2007-08-29
forum: Programming Talk
---

### Post by Thyme on 2007-08-29
Hello:

This is my first gtk program and I'm trying to align a widget in inside a table cell. The default is GTK_JUSTIFY_CENTER for widgets I think but if I try and change it then it doesn't seem to take effect.

I try the following:

label=gtk_label_new("Common Name: ");		
gtk_label_set_justify(GTK_LABEL(label), GTK_JUSTIFY_LEFT);
gtk_table_attach(GTK_TABLE(table), label, 0, 1, 0, 1, 0, 0, 0, 0);		
gtk_widget_show(label);

placing the second line before or after attaching the label to the table doesn't make a difference.

Thanks :)

---

