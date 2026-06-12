---
title: "Trying to build a deb for my anjuta application"
date: 2008-03-06
forum: Packaging and Compiling Programs
---

### Post by sharperguy on 2008-03-06
Hi.

I have written an application in anjuta which compiles fine and I have finished as much as I am going to for this version.

What I would like to do now is build a .deb for ubuntu gutsy.

I have had a look at the package guide in the ubuntu help but it doesn't seem to be very relevant.

Also, when I create a tarball with anjuta, it does not put the intltool files into the package so ./configure fails until you copy them in manually.

Any help and advice appreciated, thank you.

---

### Post by sharperguy on 2008-03-07
Ok I managed to make a package using debuild.

However I don't think anjuta created the tarball very well.

The main problem is that the program didn't really know where to look for the ".glade" file so it didn't run at all (this might be my fault but I don't really know what to do about it).

There was no rule for distclean in the makefile so when I removed it and tried to run it it said file "file not found" instead of "command not found".

Also I still don't know why the intltool files weren't copied in.

Finally, I'm still not sure how to go about creating an icon in the gnome menu.

Any advice appreciated :)

---

