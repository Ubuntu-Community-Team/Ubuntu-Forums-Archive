---
title: "unable to find vtk files"
date: 2019-11-15
forum: Packaging and Compiling Programs
---

### Post by lragan2 on 2019-11-15
Trying to install libraries for a EM Field Solver routine, I execute the following suggested directive:
sudo apt-get install build-essential git cmake libhdf5-dev libvtk5-dev libboost-all-dev libcgal-dev libtinyxml-dev libqt4-dev libvtk5-qt4-dev

Results: (after entering root pswd:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libvtk5-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libvtk7-dev:i386 libvtk6-dev:i386 libvtk7-dev libvtk6-dev

Package libvtk5-qt4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libvtk5-dev' has no installation candidate
E: Package 'libvtk5-qt4-dev' has no installation candidate

Then run the same command substituting libvtk7-dev for libvtk5-dev:
sudo apt-get install build-essential git cmake libhdf5-dev libvtk7-dev libboost-all-dev libcgal-dev libtinyxml-dev libqt4-dev libvtk5-qt4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libvtk5-qt4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libvtk5-qt4-dev' has no installation candidate

I found the following: [https://packages.ubuntu.com/xenial/amd64/libvtk5-qt4-dev/download](https://packages.ubuntu.com/xenial/amd64/libvtk5-qt4-dev/download), and perused it.  Tried to install just the libvtk5-qt4-dev using apt:

~$ sudo apt-get install  libvtk5-qt4-dev
[sudo] password for lawrence:        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libvtk5-qt4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libvtk5-qt4-dev' has no installation candidate

So, I am rather stuck.  All help is appreciated.  Thanks in advance...

---

### Post by lragan2 on 2019-12-01
Visualization Toolkit has been upgraded, and the version 5 files are no longer used.

Modified the command to:

sudo apt-get install build-essential git cmake libhdf5-dev libvtk7-dev  libboost-all-dev libcgal-dev libtinyxml-dev libqt4-dev libvtk7-qt-dev

This worked.  Case closed.

---

