---
title: "[SOLVED] Is &amp;quot;fake_expose_widget&amp;quot; a gtk function?"
date: 2008-06-22
forum: Programming Talk
---

### Post by days_of_ruin on 2008-06-22
And if so what would its pygtk equivalent be?
I saw this in some source code.

---

### Post by stroyan on 2008-06-22
It looks like an internal function to certain applications.
You can see references to and definitions of such functions using
google codesearch-

[http://google.com/codesearch?q=fake_expose_widget&hl=en&btnG=Search+Code](http://google.com/codesearch?q=fake_expose_widget&hl=en&btnG=Search+Code)

There is an interesting implementation of the function at-
[http://google.com/codesearch?hl=en&q=show:Brh1Fp4-uQw:20_PCXzks98:sRhQ5IOEbk4&sa=N&ct=rd&cs_p=http://ftp.gnome.org/pub/GNOME/desktop/2.17/2.17.3/sources/control-center-2.17.3.tar.bz2&cs_f=control-center-2.17.3/capplets/common/theme-thumbnail.c&start=1](http://google.com/codesearch?hl=en&q=show:Brh1Fp4-uQw:20_PCXzks98:sRhQ5IOEbk4&sa=N&ct=rd&cs_p=http://ftp.gnome.org/pub/GNOME/desktop/2.17/2.17.3/sources/control-center-2.17.3.tar.bz2&cs_f=control-center-2.17.3/capplets/common/theme-thumbnail.c&start=1)

---

