---
title: "[Gtkmm]How to get default font size and family?"
date: 2010-12-12
forum: Programming Talk
---

### Post by t1497f35 on 2010-12-12
Hi,
System->Preferences->Appearance->Fonts shows the default fonts in Gtk/Gnome, and all apps including Nautilus are using them.
How do I get them or just a single "default" font?

My app uses Pango to draw text and it doesn't default to the default font family and size so I need to figure out the default font and size and set these values manually.

Any ideas/hints?

---

### Post by Vaphell on 2010-12-12
my lame idea is: read settings from ~/.gconf/desktop/gnome/interface/%gconf.xml

of course some proper use of dedicated class/method would be better but i am not familiar with gtk so can't tell how to do it the right way.

---

### Post by t1497f35 on 2010-12-12
Thanks, I've found Gtk::Settings but it returns a string containing the font name and size lumped together and one has to parse it, not handy at all, but it's better than nothing.

---

