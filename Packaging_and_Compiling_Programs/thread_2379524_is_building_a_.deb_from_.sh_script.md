---
title: "is building a .deb from .sh script"
date: 2017-12-06
forum: Packaging and Compiling Programs
---

### Post by larka51-aol on 2017-12-06
Is building a .deb from a .sh package the same as building a .deb from source? I'm trying to make a .deb package using Ubuntu 16.04 from a netbeans.sh package.

---

### Post by faraco2 on 2017-12-07
Generally yes, but it also depends on how the program installation perfoms (GUI or can be invoked with just a single command that handle the rest?).

Eitherway, you can take a look at how netbeans 8.1 IDE packaged as .deb for Ubuntu 16.04 as your reference here - [https://developer.gnome.org/gtk3/stable/gtk-getting-started.html#id-1.2.3.5](https://developer.gnome.org/gtk3/stable/gtk-getting-started.html#id-1.2.3.5)

---

