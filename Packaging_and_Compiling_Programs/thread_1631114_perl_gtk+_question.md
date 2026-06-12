---
title: "perl gtk+ question"
date: 2010-11-26
forum: Packaging and Compiling Programs
---

### Post by pythonsyntax on 2010-11-26
What  headers or files do i need to install gtk+ from cpan for perl 5.12.2


Do i need cairo haders and pango headers and gtk2 headers?

---

### Post by pythonsyntax on 2010-11-26
anyone?

---

### Post by SevenMachines on 2010-11-26
Sorry if i'm confused, it is friday :) But by gtk+ do you not just meant the Gtk2 module?

For cpan,
Gtk2 : [http://search.cpan.org/~tsch/Gtk2-1.222/Gtk2.pm](http://search.cpan.org/~tsch/Gtk2-1.222/Gtk2.pm)
Deps:  [http://deps.cpantesters.org/?module=Gtk2;perl=latest](http://deps.cpantesters.org/?module=Gtk2;perl=latest)

[EDIT] Sorry, just noticed the links werent working

---

### Post by Yellow Pasque on 2010-11-26
libgtk2-perl package will pull libpango-perl and libcairo-perl packages.

---

### Post by pythonsyntax on 2010-11-26
That all i need?

---

### Post by SevenMachines on 2010-11-26
As [Temüjin]("http://ubuntuforums.org/member.php?u=327594") mentioned, unless your experienced and have some special reason to use cpan, i would generally say use the repository package instead, itll pull in the dependencies it needs too so you dont need to chase down extra packages

$ sudo apt-get install libgtk2-perl

---

### Post by pythonsyntax on 2010-11-27
root@losthost:~# apt-get install libgtk2-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2-perl is already the newest version.
The following packages were automatically installed and are no longer required:
  libterm-readline-gnu-perl libmpich1.0gf libio-string-perl
  libstring-koremutake-perl libpadwalker-perl libb-keywords-perl
  libyaml-syck-perl libparams-validate-perl libproj0 fftw2 libgfortran3
  libclass-accessor-perl libreadonly-xs-perl libclass-accessor-chained-perl
  libexception-class-perl linux-headers-2.6.35-22 liberror-perl libopengl-perl
  libdata-optlist-perl libparams-util-perl linux-headers-2.6.35-22-generic
  libdevel-symdump-perl libtree-dagnode-perl libreadonly-perl
  libfile-which-perl libio-stringy-perl libdevel-stacktrace-perl libhdf4-0-alt
  libsub-name-perl libsub-install-perl proj-data libclass-inner-perl
  libtask-weaken-perl libcsiro0 libpod-spell-perl libexporter-tidy-perl
  libclone-perl perl-tk libclass-data-inheritable-perl libconfig-tiny-perl
  libproc-background-perl libplplot9 libsub-uplevel-perl libstring-format-perl
  libppi-perl libsub-exporter-perl libqhull5 liblist-moreutils-perl
  libfile-homedir-perl freeglut3 libgetopt-long-descriptive-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by pythonsyntax on 2010-11-27
i think like this apt-get build-dep?

---

### Post by SevenMachines on 2010-11-28
$ sudo apt-get install libgtk2-perl

Means "install the libgtk2-perl library and all its dependences", use this when you want to write code that uses this library.

$ sudo apt-get build-dep libgtk2-perl

Means "install all of the libraries i need to *build* libgtk2-perl", you use this when you want to build libgtk2-perl yourself, usually when you are making changes/bugfixes to the library.

So as far as i can see you should have all you need to use gtk in your perl program, although i dont use perl myself so...

---

