---
title: "Can I put widgets over a drawing area?(gtkmm)"
date: 2008-08-03
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-08-03
It's me again :D

I am using gstreamer and gtkmm. I display my video on a Gtk::DrawingArea. And I wonder if can put other widgets(eg buttons) over the DrawingArea. Making the DrawingArea behave like a "container". Is this possible?

---

### Post by xelapond on 2008-08-03
Are you doing this in C++?

I am a Python/Qt person, but I see no reason why you could not.  You just have to show it after the drawing area, and it should appear on top.

If that fails, you could always subclass it and make a container.

Though, Python and Qt are arguably opposite of Gtk and C++:D

---

### Post by SledgeHammer_999 on 2008-08-04
Nice ideas. I'll try them out and see!!!

---

