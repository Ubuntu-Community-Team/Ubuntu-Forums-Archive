---
title: "Creating .deb for shared libraries using dh_make/debuild"
date: 2011-08-15
forum: Packaging and Compiling Programs
---

### Post by schander on 2011-08-15
I'm trying to package a shared library using debuild to build the .deb file. In runnign dh_make the library option was selected. Have been following this [guide.]("http://wiki.ubunut.com/PackagingGuide/Complete") Having managed to build the library, i'm getting the foillowing error:
```

  dh_install
dh_install: mylibrary-dev missing files (usr/lib/lib*.a), aborting
make: *** [binary] Error 255
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```I looked inside the directory listed in the error, e.g. ~/mylibrary-1.0/debian/mylibrary-dev/usr/lib/ and it empty. The shared libraries are actually in: ~/mylibrary-1.0/debian/tmp/usr/lib/ However there are no *.a libs in there. The mylibrary-dev.install file list the following:

```
usr/include/*
usr/lib/lib*.a
usr/lib/lib*.so
usr/lib/pkgconfig/*
usr/lib/*.la
usr/share/pkgconfig/*
```
For some reason an extra package is listed in the control file.

```
Source: mylibrary
Priority: extra
Maintainer: satpal <satpal@unknown>
Build-Depends: debhelper (>= 7.0.50~), autotools-dev
Standards-Version: 3.8.4
Section: libs
Homepage: <insert the upstream URL, if relevant>

Package: mylibrary-dev
Section: libdevel
Architecture: any
Depends: mylibrary1 (= ${binary:Version})
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>

Package: mylibrary1
Section: libs
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>
```

My rules file is:

```
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

%:
    dh $@
```
Following the helloworld example used in the guide, it only comes up with Source and a single package

Sorry for long post, just wanted ensure there was enough info.
I have attached a simple example using the Makefiles from the original project to show the error. What i did to reproduce the error. In the debsharedlib-1.0 folder issue the following commands:
[LIST=1]
[*]dh_make
[*]in the debain folder: rm *.ex *.EX
[*]debuild (also in the debain folder)
[/LIST]

Thanks
Satpal

---

### Post by schander on 2011-08-16
I managed to work this out. I was all my fault. I had put:
```
AM_DISABLE_STATIC
```
In my configure.ac file which meant I got no static libaries (*.a) files built.

Thanks

---

