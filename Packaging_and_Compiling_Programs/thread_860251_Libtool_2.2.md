---
title: "Libtool 2.2"
date: 2008-07-15
forum: Packaging and Compiling Programs
---

### Post by pocketchange on 2008-07-15
I'm trying to go through a tutorial for libtool to learn it's functionality so I can easily write shared libraries.  This is the tutorial I'm doing:

[http://www.freesoftwaremagazine.com/books/agaal/building_shared_libraries_once_using_autotools](http://www.freesoftwaremagazine.com/books/agaal/building_shared_libraries_once_using_autotools)

I found that Ubuntu repositories only contain libtool 1.5 (as mentioned in the tutorial).  I'd like to get 2.2 running, so I downloaded and built it.  I tried installing everything with:

./configure --prefix=/opt/libtool-2.2

but found that it couldn't expand the Macro LT_PREREQ([2.2]) in my configure.ac.

I tried doing just a ./configure to see if the default install location would work, which is /usr/local.  This doesn't appear to work either.  I'm a bit afraid to do install into the normal /usr folder using:

./configure --prefix=/usr

Is this going to blow away any configurations I have there?  Is this even going to work?

Is there a .deb out there somewhere I can install?  A search through the Ubuntu packages reveals no libtool 2.2.

---

### Post by pocketchange on 2008-07-16
I went ahead and took the plunge:

$ sudo apt-get remove libtool
$ cd libtool-2.2
$ ./configure --prefix=/usr --enable-ltdl-install
$ make
$ make install

This appears to work.  Now my macros expand as expected.  I'm a bit uncertain as to why there's no libtool-2.2 in the repositories anywhere...

---

