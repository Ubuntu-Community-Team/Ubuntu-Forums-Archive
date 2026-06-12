---
title: "Integration between Glade and C code"
date: 2007-10-26
forum: Programming Talk
---

### Post by TKE Super Dave on 2007-10-26
Hello I'm new so please take it easy on me.

I'm attempting to use the Glade to create a GUI and integrate it with some C code I have written to make a small game. I have both the C code finished and I have made the GUI using Glade, but I have no clue how to connect the two. 

The things I'm trying to do are to get several buttons on the GUI to send info to the code so that certain actions can be taken. I'm also trying to get it so that a new picture is shown on the GUI once the code reaches a certain point, and finally I'm trying to make it display a score function. 

 I have been unable to find examples using a simple search on google and on this and Glade's website. I would greatly appreciate it if someone could point me in the directions of some tutorials or examples or tell me how to do so. 

Thanks,
TKE Super Dave

---

### Post by jespdj on 2007-10-26
So you have a .glade file, which contains the XML definition of your user interface. You need libglade to load that in your C program.

[http://library.gnome.org/devel/libglade/2.6/](http://library.gnome.org/devel/libglade/2.6/)
[http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)

Ofcourse you'll also have to know how to program the GUI using GTK:

[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)

---

