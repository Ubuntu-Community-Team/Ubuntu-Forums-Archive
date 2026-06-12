---
title: "upgrade GLIB, Pango and GTK+ libraries (how to ?)"
date: 2011-11-29
forum: Packaging and Compiling Programs
---

### Post by drBouvierLeduc on 2011-11-29
Hi, 

This may seems like a trivial question, but it puzzles me !
So monthly, I like to compile GIMP in order to test the latest and greatest features.
Recently GIMP 2.7.x [updated some dependancies]("http://git.gnome.org/browse/gimp/commit/?id=367354925763fba163ead17c0c7a8eb03514579b"), which are unfortunately not available on ubuntu 11.10 : 
> Depend on lots of newer library versions
Gegl >= 0.1.8, Babl >= 0.1.6, Gdk-Pixbuf >= 1.24.0, Pango >= 1.29.4, GLib >= 2.28.8, GTK+ >= 2.24.7  Which means depending on a gazillion of bug fixes, which means less pain for GIMP 2.8 users, and less useless bugzilla traffic eating developer resources 
So I downloaded those libraries, compiled and installed them the standard way (./configure, make and checkinstall).
Unfortunately, Ubuntu didn't like this : no more theme, no more icon etc... some conflict between the new and the old libgtk+ I guess.

The thing is, Those libraries are installed *alongside* the old ones, whereas I would like them to *replace* the old ones.
I know how to do this via synaptic, but not with the command line.
Any advice ?

Thanks in advance.

---

### Post by SevenMachines on 2011-11-30
./configure, make and checkinstall usually creates packages that install by default to /usr/local, chances are some of these at least have replaces the system packages, depends on the default name checkinstall generated. With some of the packages mentioned key components this is very likely to cause problems.
Short answer is that its not trivial to update things like gtk system-wide easily without updating a whole lot of other stuff.

---

### Post by Bachstelze on 2011-11-30
If you really want to, the best way would be to get the Ubuntu source packages for the packages you want to install, and rebuild them with the newer version of the source code. No guarantee it will work, but it's probably your best bet (besides using another distro altogether). If a package you want exists in Precise, you can also try to install that (no guarantee either).

---

### Post by drBouvierLeduc on 2011-11-30
Thanks for your answers.
Well, it turns out SevenMachines was right, messing with GTK libs was NOT a good idea !
I managed to screw up my system for good, I'm reinstalling ubuntu atm.

Unfortunately those libs are not updated in precise yet, so I'll guess I'll pause compiling and use matthaeus's ppa for the time being...

---

