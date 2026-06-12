---
title: "Input/ouput data  Glade"
date: 2009-07-27
forum: Programming Talk
---

### Post by J-cizzle on 2009-07-27
Hey everyone,

I'm relatively new to programming in general but I'm supposed to design a gui for one of my professors and I'm having some trouble. 

I'm supposed to create a gui that takes some numerical inputs from entry boxes and maybe have a drop-down selection menu and the data should be sent to a .dat file that can be used by his program. My problem lies in the data output. I can't seem to figure out how to take the data from the entry boxes and send them to the file. I have the C code to send data to files, but can't seem to link glade and C. Any help would be greatly appreciated.

J-Cizzle

---

### Post by ggaaron on 2009-07-28
I've never used Glade/GTK+ with C, but you should use GtkBuilder to link C code and GUI.
[http://library.gnome.org/devel/gtk/unstable/GtkBuilder.html](http://library.gnome.org/devel/gtk/unstable/GtkBuilder.html)
You'll probably find some tutorials.

I haven't used GtkBuilder myself, I only used older libglade (it can still be used, GtkBulder is preferred though) so I can tell you how to set up GUI and take data from widgets using it if you'd like.

Happy Hacking

---

