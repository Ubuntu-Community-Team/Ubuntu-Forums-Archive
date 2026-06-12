---
title: "how do you compile a XML file in C++?"
date: 2013-01-19
forum: Programming Talk
---

### Post by carcinoGeneticist on 2013-01-19
good day, im having this issue right now

ive made a GUI in Glade and saved it as a XML, i want to use this interface in my C++ program, but ive failed miserably over and over again, ive tried to download many libraries already with no luck

could somebody please give me a hand here and also provide the full list of dependencies i need to do this?

---

### Post by MG&amp;TL on 2013-01-20
First install *gtkmm*, the C++ library for GTK+. It's available in the package *libgtkmm-3.0-dev*, I believe, or similiar.

Then use [http://developer.gnome.org/gtkmm-tutorial/unstable/chapter-builder.html ]("http://developer.gnome.org/gtkmm-tutorial/unstable/chapter-builder.html")

...and follow along to load the file. :)
[]("http://developer.gnome.org/gtkmm-tutorial/unstable/chapter-builder.html")

---

