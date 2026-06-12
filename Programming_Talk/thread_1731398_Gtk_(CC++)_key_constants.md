---
title: "Gtk (C/C++) key constants"
date: 2011-04-17
forum: Programming Talk
---

### Post by t1497f35 on 2011-04-17
Hi,
I'm using Gtkmm/Gdkmm and can't find the constants for key events (like the arrow up key, tab key, etc etc) for using with C++ with Gtk. It should look like **GDK_arrow_up or GDK::arrow_up** etc.

All I found on the internet was stuff about the python backend. Can anyone please point to an URL with the Gtk/Gdk C++ (or at least C) key constants?

---

### Post by dwhitney67 on 2011-04-17
I believe the file you seek is gtkenums.h, which is located in /usr/include/gtk-2.0/gtk.

You should not have to include this header file directly; it is included within gtk.h, and more relevant to you, via gtkmm.h (which includes gktmm's window.h).

In conclusion, only include <gtkmm.h>, and use the gtkenums.h file for reference purposes only.

---

### Post by t1497f35 on 2011-04-17
Thanks, since you seem knowledgeable, do you happen to know how to detect that the user has pressed the "A" key (the key on the keyboard to the right of the "Caps lock" key) regardless of the current keyboard/language layout?
The problem is that Gtk reports it based on the keyboard layout, so if I click "A" but the keyboard/language layout is Russian - I get the Russian key/letter "&#1060;" which is not what I want, since i.e. I want to create a game with (the rather typical) ASWD navigation, thus the navigation will stop working properly if the user is using a non-english keyboard/language layout.

---

### Post by dwhitney67 on 2011-04-17
> **t1497f35 said:**
> Thanks, since you seem knowledgeable...

I'm not very knowledgeable with Gtk, much less Gtkmm.  I've dabbled with the latter, but I had drop it in lieu of using Xlib/Motif.  Searching for an enum, though, was trivial; all I did was find the Gtk header files, and use grep to search for the string you requested.

I wish I could help you with your more pressing problem, however I would not know what to suggest, due to my lack of knowledge of Gtkmm.

---

### Post by cgroza on 2011-04-17
> **t1497f35 said:**
> Thanks, since you seem knowledgeable, do you happen to know how to detect that the user has pressed the "A" key (the key on the keyboard to the right of the "Caps lock" key) regardless of the current keyboard/language layout?
The problem is that Gtk reports it based on the keyboard layout, so if I click "A" but the keyboard/language layout is Russian - I get the Russian key/letter "&#1060;" which is not what I want, since i.e. I want to create a game with (the rather typical) ASWD navigation, thus the navigation will stop working properly if the user is using a non-english keyboard/language layout.
wxWidgets provides a way to get the key code, then it is enough to look at an ASCII table. Gtkmm should provide a similar function.

---

