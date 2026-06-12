---
title: "Gtk-WARNING **: Locale not supported by C library"
date: 2008-08-18
forum: Programming Talk
---

### Post by hamid206 on 2008-08-18
I used glade to design my program interface and wrote my interface writings in a local language . so the textes and widget direction be in RTL . but when I run the program it dosent show texts and widgets in RTL and send this massage Gtk-WARNING **: Locale not supported by C library. while I have local language in my system . what should I do to solve this problem ?

---

### Post by WW on 2008-08-18
If someone here knows the answer, I'm sure they will be happy to help, but you might get a faster response from one of the [GTK+ mailing lists](http://www.gtk.org/mailing-lists.html), perhaps [email]gtk-list@gnome.org[/email] or [email]gtk-i18n-list@gnome.org[/email].

---

### Post by mssever on 2008-08-18
I had that problem a while back, but with many different programs. It was caused by the fact that I'd backported a newer version of libc and didn't have whatever else I needed. The only way to fix it was to downgrade libc to Ubuntu's version for the release I was running at the time (I don't remember whether it was dapper or edgy).

---

