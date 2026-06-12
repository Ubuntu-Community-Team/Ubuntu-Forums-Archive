---
title: "[SOLVED] Python gnome.ui.Druid quit command"
date: 2008-09-05
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2008-09-05
Hi, 
my program has a menu with "new druid" sub item in file, so
can I Kill the Druid from the cancel button, cause from default in a tutorial from where I got the Druid as an working example it had gtk.main_quit, can something else be putted instead it ?

Thanks in advance.

---

### Post by DamjanDimitrioski on 2008-09-06
I solved it, it has gtk.Window and I just set window.destroy() and it  exits now.

---

