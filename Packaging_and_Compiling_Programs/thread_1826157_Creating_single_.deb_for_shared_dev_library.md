---
title: "Creating single .deb for shared dev library"
date: 2011-08-16
forum: Packaging and Compiling Programs
---

### Post by schander on 2011-08-16
After working howto build .deb package for shared objects.
I find that I several .deb packages:
```
mylibrary-dev_1.0-1_i386.deb
mylibrary1_1.0-1_i386.deb
mylibrarydep_1.0-1_i386.deb
```
Where the first one has the header files required to use the lib. The second has the actual library & the third has the lib that mylibrary depends on which is a completly seperate package with it own autoconf config files. I have included it using AC_CONFIG_SUBDIRS in the mylibrary configure.ac.

It seems as though I can't install the dev .deb file unless I have installed the mylibrary1 .deb file and the dependancy library will also need to be installed.

My question is how can I package these up into 1 deb file which will install everything?

Thanks

---

### Post by SevenMachines on 2011-08-16
This looks like a better explanation than i could string together
[http://www.netfort.gr.jp/~dancer/column/libpkg-guide/libpkg-guide.html#shldevpackagecontents]("http://www.netfort.gr.jp/%7Edancer/column/libpkg-guide/libpkg-guide.html#shldevpackagecontents")

Note that you may not want/need/have all the default files in the dh_make generated .install files, pkgconfig files for example, if you dont then you need to remove them.

In a very basic sense you might have a source library 'mylibrary'. You should end up with 2 packages from your control file, something like
* libmylibrary1
containing the runtime library
/usr/lib/libmylibrary.so.1.0.1

and the symlink
/usr/lib/libmylibrary.so.1 -> /usr/lib/libmylibrary.so.1.0.1
to that library

* libmylibrary-dev, depends on libmylibrary1
contains headers /usr/include/mylibrary/*.h 
and symlink to runtime library
/usr/libmylibrary.so -> /usr/lib/libmylibrary.so.1.0.1

[EDIT] The above is a bit hazy but I think its right!

---

