---
title: "Theme Parsing Error"
date: 2016-01-15
forum: New to Ubuntu
---

### Post by Gabriel_Saul on 2016-01-15
Hello. Brand new Ubuntu user checking in (3 days since installing).

I've been using Ubuntu for development, and have mainly been tinkering with gedit and the GCC compiler within the terminal for writing C source files, compiling and running them.

Recently, I ran into a string of GTK warnings about a theme parsing error upon opening gedit or a gedit file, specifically "junk at end of value". This seemed to occur after installing and removing a theme editing application from the software centre called "Theme Configuration". Here is the output:

```
(gedit:2721): Gtk-WARNING **: Theme parsing error: gtk.css:27:35: Junk at end of value

(gedit:2721): Gtk-WARNING **: Theme parsing error: gtk.css:40:48: Junk at end of value

(gedit:2721): Gtk-WARNING **: Theme parsing error: gtk.css:48:46: Junk at end of value

(gedit:2721): Gtk-WARNING **: Theme parsing error: gtk.css:59:58: Junk at end of value

(gedit:2721): Gtk-WARNING **: Theme parsing error: gtk.css:70:46: Junk at end of value

(gedit:2721): Gtk-WARNING **: Theme parsing error: gtk.css:81:58: Junk at end of value


```

What do these warnings indicate and how would I go about fixing the issue that causes them to appear?

Thank you,

GS

---

### Post by vasa1 on 2016-01-15
See [http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications/](http://askubuntu.com/questions/422254/why-are-there-so-many-console-messages-from-gtk-applications/) for answers and links that may of interest.

---

### Post by teemu-leisti on 2016-06-26
These particular lines seem to be due to a bug reported here: [https://bugs.launchpad.net/ubuntu/+source/gtk-theme-config/+bug/1500210](https://bugs.launchpad.net/ubuntu/+source/gtk-theme-config/+bug/1500210)

Aside from outputting clutter into your terminal, this seems to be harmless.

While waiting for a fix from upstream, the way you can get rid of these warnings is to edit your ~/.config/gtk-3.0/gtk.css file, and add the missing semicolons in those places indicated by the warnings, that is, on lines 27, 40, 48, 59, 70, and 81. I just tested this and can confirm it works.

---

