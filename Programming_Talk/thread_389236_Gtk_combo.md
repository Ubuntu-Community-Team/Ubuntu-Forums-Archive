---
title: "Gtk combo"
date: 2007-03-20
forum: Programming Talk
---

### Post by bradleyd on 2007-03-20
Hello everyone,
I am stuck on a Gtk combo. I have this code below on a button signal connect.
```
val = gtk_entry_get_text(GTK_ENTRY(GTK_COMBO(data->combo)->entry));
  if ( val == "Support Alpha" ){
    printf("hi1"\n);
  }
  else if (val == "Support Bravo"){
     printf("hi2"\n);
  }
  else if ("val == "Support Charlie"){
     printf("hi3"\n);
  }
```
There are three entries in the combo box. When the user selects one and the presses button I need to distinguish between which one the user selected.
any help would be appreciated.
Thanks,
brad

---

### Post by -Rick- on 2007-03-22
See [this]("http://c-faq.com/charstring/stringeq.html") link on howto compare strings in C.

---

### Post by bradleyd on 2007-03-22
thanks, that worked perfectly.

---

