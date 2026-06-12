---
title: "Installing GTK+"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by Adam Jensen on 2012-01-03
Hello everyone,

I've downloaded GTK+ and all of its dependencies and I am experiencing difficulties installing it. I followed the instructions on this site -->[http://developer.gnome.org/gtk3/stable/gtk-building.html](http://developer.gnome.org/gtk3/stable/gtk-building.html)

I am currently stuck on the step that asks you to run the following command in the terminal: ./configure --prefix=/opt/gtk.
This is part of the output in my terminal when I run that command:



```
No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
adamjensen@ubuntu:~/Desktop/gtk+-3.2.3$
```




Am I supposed to add the directories for the dependencies in the source code for GTK+? If so, where? Am I supposed to install the dependencies as well? If anyone could provide a detailed step-by-step explanation of what I'm supposed to do, it would be appreciated. The gnome site has not helped one bit.

-Adam Jensen 

PS- I'm new to Ubuntu and Linux, so if my questions sound noobish and make you want to preform a facepalm, please forgive me :D.

---

### Post by thig1002 on 2012-01-03
Apparently, [Adam Jensen]("http://ubuntuforums.org/deusex.wikia.com/wiki/Adam_Jensen") hasn't upgraded his "computer hacking" skills :P 

I'm sorry, I saw the name and had to crack a joke. 

Why not get a prebuilt binary package?

---

### Post by Adam Jensen on 2012-01-03
The local LIMB clinic ran out of Praxis kits :D

Binary package? Where could I find one? Link please!

---

### Post by mcduck on 2012-01-03
> **Adam Jensen said:**
> The local LIMB clinic ran out of Praxis kits :D

Binary package? Where could I find one? Link please!

Use Ubuntu's package management tools. The Ubuntu Software Center, Synaptic Package Manager, or apt-get from command line.

In general downloading stuff from random web pages is the last thing you'd try on Linux systems, the package management will download and install (and update, uninstall, reconfigure etc) everything automatically for you.

Anyway, is there a specific reason why you are trying to install GTK+? It's horribly outdated (has been for almost 10 years now) and pretty much everything is using GTK2 or GTK3 instead (which are both installed by default).

edit: Oh, the guide is actually for GTK3, not GTK1. In that case you don't need to do anything, *you already have GTK3*. :)

---

### Post by Adam Jensen on 2012-01-03
I want to use GTK to create user interfaces for programs written in C/C++. Huh? I already have GTK? How do I use it? I feel so stupid! lmao

---

### Post by mcduck on 2012-01-03
> **Adam Jensen said:**
> I want to use GTK to create user interfaces for programs written in C/C++. Huh? I already have GTK? How do I use it? I feel so stupid! lmao

If you want to use it for programming, it's the *development package* with development headers and libraries you'll need, not the normal package which you already have,

Just install the [libgtk-3-dev]("apt:libgtk-3-dev") package.

---

### Post by Adam Jensen on 2012-01-03
Oh! I get it now! Please forgive me for my...."slowness". I was expecting an IDE of some sort. I did not know that GTK was just a bunch of libraries and header files :P. I already have libgtk-3-dev installed. Thank you for helping me to understand this. Have a great night.):P

---

