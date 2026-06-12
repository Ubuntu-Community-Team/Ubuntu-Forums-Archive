---
title: "Setting a GtkCheckButton to 'checked' by default"
date: 2012-10-27
forum: Programming Talk
---

### Post by notgary on 2012-10-27
I'm working on some Gtk code written by someone else as a way of 'diving into' the platform head first, and I'm trying to figure out how to set a GtkCheckButton to be checked when the application starts. Can anyone please show me how to do this in both C code and with Glade?

---

### Post by alexfish on 2012-10-28
gtk_toggle_button_set_active(long,int)

long is the id of the widget
int is the vaue , TRUE =1 , FALSE = 0

check and radio are part of the same family of toggle

Regards

Alex

---

### Post by notgary on 2012-10-29
Thanks a lot :)

---

