---
title: "Package a data file (no source/binary)"
date: 2008-02-02
forum: Packaging and Compiling Programs
---

### Post by trainpic on 2008-02-02
I want to package a data file (specifically: a soundfont for fluidsynth/qsynth) to put in my PPA. I am not sure how to do this, as I have no idea how to create a "source" package for a data file. I also cannot imagine what form "building" would take for something like this...

---

### Post by dholbach on 2008-02-04
Check out [http://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages](http://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages) and of course [http://wiki.ubuntu.com/PackagingGuide/Complete](http://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by trainpic on 2008-02-24
Thanks.
Already read the package guide, and it says nothing about data packages. Any other suggestions?

---

### Post by plugwash on 2008-02-24
there are a couple of examples listed in the referencepackages section of the guide under "simple installation of data" which sounds like what you want.

A source package usually consists of a .orig.tar.gz containing the stuff from upstream and a .diff.gz containing the debian dir and any changes you made. You can also have a "debian native" package where the complete debianised source tree is in the source file.

The upstream tarball can contain anything. The diff.gz can only contain text files. If you need to include some binary data in a diff.gz you can always use uuencoding and do a uudecode as part of the build process.

now for how a package is built (assuming the simple case of a package that builds only one binary, things get a little tricker when you get mixed arch all and arch any packages and some other unusual cases)

dpkg-buildpackage does roughly the following sequence
debian/rules clean
call dpkg-source to build the source package
debian/rules build
debian/rules binary

the clean target cleans everything up ready for doing a fresh build or producing a new source package.
the build target builds the software (usually via the build-stamp target which leaves a stamp to show building is already completed). What this involves depends on what is being packaged. It may need to compile source, it may need to uudecode stuff, it may need to do image maniupulation using a tool like imagemagick. IT MAY NOT NEED TO DO ANYHING AT ALL!
the binary target copies the files from the build to a dummy tree (typically via depending on a seperate install target), sets up permissions on it (usually done by using /usr/bin/install ) and then calls various stuff related to actually building the debs.
 
the clean and binary targets are run as either root or fakeroot (usually fakeroot) so that the debs can be generated with correct file permissions inside..

---

