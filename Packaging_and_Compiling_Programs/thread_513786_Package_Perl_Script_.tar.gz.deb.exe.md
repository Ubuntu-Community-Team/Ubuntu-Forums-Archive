---
title: "Package Perl Script .tar.gz/.deb/.exe"
date: 2007-07-30
forum: Packaging and Compiling Programs
---

### Post by nhandler on 2007-07-30
I have created a perl script that uses the Gtk2 module to create a GUI. I now wish to package up the perl script into either a .tar.gz with a makefile or a .deb. I've read through a lot of the wiki pages on creating .deb files, but my problem will be the control file.

Since this script would also be useful on Windows, I would also like to package it in an exe.

Is there any easy way to go about this?

---

### Post by tr333 on 2007-07-31
If you want a self-executing perl program, take a look at the [Perl Packager](http://par.perl.org/).

---

