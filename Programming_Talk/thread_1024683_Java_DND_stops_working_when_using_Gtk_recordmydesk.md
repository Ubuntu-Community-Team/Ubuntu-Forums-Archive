---
title: "Java DND stops working when using Gtk recordmydesktop"
date: 2008-12-29
forum: Programming Talk
---

### Post by cl333r on 2008-12-29
Hi folks,
I just noticed that drag and drop (DND) stops working in Java (6 update 10) swing components on my Ubuntu 8.10 when the application to record the desktop "Gtk recordmydesktop" is working (i.e. is recording). The Java applications just don't receive any DND events. I can't figure out a workaround because there are no DND events and thus no idea how to fix except to not record.
Did anyone come across this as well?

After I shut down that application, the Java components start receiving DND events and DND starts working.

---

