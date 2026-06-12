---
title: "[SOLVED] What does &amp;quot;choosing an appropriate prefix&amp;quot; mean?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-07-03
I am trying to compile the Epiphany web browser so the it runs with webkit. I went [here]("http://live.gnome.org/WebKitGtk") to compile WebKit/GTK+ first, but I don't understand what it means on Building the Sources. Can someone explain what that means, and how I can find what prefixes to use/are available?

---

### Post by Daveth on 2008-07-03
are not the 3 examples beneath the 

./autogen.sh --prefix=/usr/local
make

terminal, the prefixes? In other words, they alter the base installation to do extra things, like using libsoup.
So the text

Run the following commands to configure and build WebKit (choosing an appropriate prefix):

flags up that there are options beyond the standard build, so that you can customise it. Well, that's how I read it!

---

