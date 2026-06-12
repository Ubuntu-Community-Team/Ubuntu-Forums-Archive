---
title: "Ruby GTK how to lock a GTK::Paned widget"
date: 2008-06-29
forum: Programming Talk
---

### Post by Questioneer on 2008-06-29
Hello-
I would like to lock the position of a GTK::Paned widget in Ruby/GTK.

How would I do this?

Thanks.

---

### Post by Questioneer on 2008-06-29
Forgot to mention: I'm using Ubuntu 8.04 with the latest versions of Ruby and GNOME.

---

### Post by napsy on 2008-06-29
That is not possible since the paned is used especially for changing the dimensions of the widgets. If you want to "lock" the widgets use boxes or tables.

---

