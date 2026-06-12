---
title: "Compiling GTK+ Applications"
date: 2012-12-24
forum: Programming Talk
---

### Post by madnag4u on 2012-12-24
Hello. I wanted to start GTK+ application programming and I was following this tutorial: [http://developer.gnome.org/gtk-tutorial/2.90/c39.html](http://developer.gnome.org/gtk-tutorial/2.90/c39.html)

When I run 
```
pkg-config --cflags --libs gtk+-2.0
```I get the following error
```
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
```Please help.

Incidentally, can we also use gtk+-3.0 to create apps in Quantal?

---

### Post by MG&amp;TL on 2012-12-24
You'll need to install *libgtk2.0-dev* in order to have the required header files for 2.x.

That said, PLEASE don't program with GTK+ 2.x: 3.x is stable, and has been for a while now. Unless you have very good reason to do so, you're just making work for yourself later. There's a similiar tutorial for 3.x here: [http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html](http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html)

...and a reference manual here: [http://developer.gnome.org/gtk3/stable/](http://developer.gnome.org/gtk3/stable/)
[]("http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html")

---

### Post by madnag4u on 2012-12-24
> **MG&TL said:**
> You'll need to install *libgtk2.0-dev* in order to have the required header files for 2.x.

That said, PLEASE don't program with GTK+ 2.x: 3.x is stable, and has been for a while now. Unless you have very good reason to do so, you're just making work for yourself later. There's a similiar tutorial for 3.x here: [http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html](http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html)

...and a reference manual here: [http://developer.gnome.org/gtk3/stable/](http://developer.gnome.org/gtk3/stable/)


Well, I'll take heed of your advice then. I've just started, so it'll be easy to switch. But I do get the same error when I link gtk+-3.0 with pkg-config. Do I then need to install libgtk3.0-dev to solve this problem?

---

### Post by madnag4u on 2012-12-24
Thank you MG&TL. Your hint to install *libgtk2.0-dev* led me to deduce that I had to install *libgtk-3-dev *in order to compile GTK 3.x apps. My code compiled successfully.

---

### Post by MG&amp;TL on 2012-12-24
> **madnag4u said:**
> Thank you MG&TL. Your hint to install *libgtk2.0-dev* led me to deduce that I had to install *libgtk-3-dev *in order to compile GTK 3.x apps. My code compiled successfully.

Awesome. :) Sorry I wasn't around, my mother was going beserk.

Good luck with GTK+, it's a great toolkit, just a bit difficult to get your head around at first.

---

### Post by SuperCamel on 2012-12-24
> **MG&TL said:**
> You'll need to install *libgtk2.0-dev* in order to have the required header files for 2.x.

That said, PLEASE don't program with GTK+ 2.x: 3.x is stable, and has been for a while now. Unless you have very good reason to do so, you're just making work for yourself later. There's a similiar tutorial for 3.x here: [http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html](http://developer.gnome.org/gtk3/3.0/gtk-getting-started.html)

...and a reference manual here: [http://developer.gnome.org/gtk3/stable/](http://developer.gnome.org/gtk3/stable/)


Gtk+ 3 might be stable but there are no official binaries for Windows yet! It's a massive pain in the rear for those developing cross platform software. Is Gtk+3 even cross platform? I know I'll be using Gtk 2 until they are released.

---

### Post by MG&amp;TL on 2012-12-25
> **SuperCamel said:**
> Gtk+ 3 might be stable but there are no official binaries for Windows yet! It's a massive pain in the rear for those developing cross platform software. Is Gtk+3 even cross platform? I know I'll be using Gtk 2 until they are released.

Still cross-platform. 

Sorry though, I thought they'd be binaries by now. :( Might be worth seeing if you can build it from source and put an unofficial release out?

---

