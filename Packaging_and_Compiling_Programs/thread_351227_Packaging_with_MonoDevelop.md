---
title: "Packaging with MonoDevelop?"
date: 2007-02-01
forum: Packaging and Compiling Programs
---

### Post by jopsen on 2007-02-01
Hey,

I've started developing .Net/Mono with MonoDevelop, and I'm currently at the point where I would like to make some packages for beta testing and later release; perhaps in the universe :)
I don't really have any experiences with GNU autotools, make or related tools...

Anyway, MonoDevelop can generate a nice tarball, just like the ones I can find else where... I've been reading the ubuntu packaging guide (the one from doc.ubuntu.com)... But I have 2 problems...

1: My tar.gz doesn't contain a makefile (never seen one that did), but I can generate the makefile with ./configure, but if I open the makefile manually with a text editor there are some paths that are NOT relative... Could this be right??? How am I suppose to generate the makefile used in the source package???
(I tried using one generated with ./configure, but it gave some kind of error, I think. Could I be missing some parameter?)

2: My other problem is that the tarball I get from MonoDevelop only compiles and installs my binaries, it doesn't add .desktop files, icons or anything else... I guess that somehow I'll be able to add these file in the diff.tar.gz (the ubuntu specific changes); but I also have to make sure that that these .desktop files and icons are copied when the makefile is executed with "make install"... Otherwise they won't be a part of the package, right?
I don't know if I have to edit the makefile.in, makefile.am, ./configure, the makefile or some other file in source package... Does anybody know how I could achieve this? Some documents, tutorials or documentation of how to edit these files would be nice too...

I hope somebody can help me, cause I'm starting to think that it might be easier to just create a binary package, without all the tools... But it wouldn't be the same :)

By the way, I'm working on a Last.fm ripper, as a school project in technology... I'll release it as soon as it's stable (or just fairly close)...

//Regards Jonas F. Jensen.

---

### Post by jopsen on 2007-02-03
Hi,

I realized that my first question isn't very good, since ./configure is suppose to be executed at build time from the /debian/rules file in the source package...
 I guess I was confused because dh_make for some wired reason wrote something like "no top level makefile found....." But I tried to use dh_make again with a cleaner source... and for some reason it didn't poste the message again...

Now I've managed to create a source package and add the correct build dependencies. When using pbuilder I can see that the configure file is executed... But the outout .deb file doesn't contain my binaries... And I stille haven't found a way to add .desktop file to the source package???

---

### Post by jopsen on 2007-02-04
Okay... I geuss I figured out howto package the whole thing... using cdbs most of the things are handled else where... 

By the way this document wasn't a bad place if anyone else is trying to package mono application: [http://pkg-mono.alioth.debian.org/cli-policy/](http://pkg-mono.alioth.debian.org/cli-policy/)
(I think/hope it applies for ubuntu as well)

---

