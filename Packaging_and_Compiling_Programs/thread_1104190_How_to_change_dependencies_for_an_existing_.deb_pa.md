---
title: "How to change dependencies for an existing .deb package?"
date: 2009-03-23
forum: Packaging and Compiling Programs
---

### Post by khm on 2009-03-23
I have a debian package for which I would like to change on of the dependencies (change *depends on: libgnome-desktop-2* to *depends on libgnome-desktop-2-11*)

How can I do this?

---

### Post by loell on 2009-03-23
while possible by unpacking, editing, then repacking the pacakge, it isn't really a good idea, oftentimes it will yield weird behaviors to the program.

---

### Post by Bachstelze on 2009-03-23
Moved to PAckaging and Compiling.

Also, some additonal background: OP has a proprietary package that was made for Intrepid, and which depends on libgnome-desktop-2. Since he wishes to install it on Jaunty, in which libgnome-desktop-2 was renamed to libgnome-desktop-2-11, I suggested in another thread that he modified the dependencies of the package (since as far as I can tell, both packages contain the same thing).

@OP: it is not at all sure it will work, by the way, but still worth a try since it's pretty much your only option.

---

### Post by khm on 2009-03-23
> **HymnToLife said:**
> Moved to PAckaging and Compiling.

Also, some additonal background: OP has a proprietary package that was made for Intrepid, and which depends on libgnome-desktop-2. Since he wishes to install it on Jaunty, in which libgnome-desktop-2 was renamed to libgnome-desktop-2-11, I suggested in another thread that he modified the dependencies of the package (since as far as I can tell, both packages contain the same thing).

@OP: it is not at all sure it will work, by the way, but still worth a try since it's pretty much your only option.

This may be a stupid question, but I cannot "package it back up" for a few reasons:

1. I'm not really sure what kind of archive a .deb is... the archive manager cannot create a .deb archive. 

2. There are 2 zip files within the .deb file (control.tar.gz and data.tar.gz).  I know that I need to modify a file within the control file, but I can't seem to archive it back up because the child directory of control is "."  How do I create a directory called "."?

---

### Post by InfinityCircuit on 2009-03-23
```
kronos:/home/dmr# aptitude show equivs
Package: equivs
New: yes
State: installed
Automatically installed: no
Version: 2.0.7-0.1
Priority: extra
Section: admin
Maintainer: Peter Samuelson <peter@p12n.org>
Uncompressed Size: 139k
Depends: debhelper (>= 4), devscripts, dpkg-dev, fakeroot, make, perl
Description: Circumvent Debian package dependencies
 This package provides a tool to create Debian packages that only contain
 dependency information. 
 
 One use for this is to create a metapackage: a package whose sole purpose is to
 declare dependencies and conflicts on other packages so that these will be
 automatically installed, upgraded, or removed. 
 
 Another use is to circumvent dependency checking.  If a package P is not
 installed on the system, packages that depend on P cannot normally be
 installed.  However, if functionality equivalent to P is known to be installed,
 this tool can be used to trick the Debian package management system into
 believing that package P is actually installed. NOTE: this should be considered
 a crude hack to work around awkward situations, not a normal solution.  If you
 use equivs to work around bugs in other Debian packages, you should also file
 bug reports against those packages.

```

---

### Post by Grumpster on 2009-05-25
> **khm said:**
> This may be a stupid question, but I cannot "package it back up" for a few reasons:

1. I'm not really sure what kind of archive a .deb is... the archive manager cannot create a .deb archive. 

2. There are 2 zip files within the .deb file (control.tar.gz and data.tar.gz).  I know that I need to modify a file within the control file, but I can't seem to archive it back up because the child directory of control is "."  How do I create a directory called "."?

I have about the same problem. I've already extracted the contents of the deb file, changed the version number of one of the dependencies. How do I put it back into a deb file. I've tried using both tar and tar.gz and renaming them to .deb but that don't work. What does work?

---

### Post by unutbu on 2009-05-25
I haven't tried this myself, but according to [http://ubuntuforums.org/showpost.php?p=7334658&postcount=6](http://ubuntuforums.org/showpost.php?p=7334658&postcount=6), the idea is to install the devscripts package and issue the command
```

sudo debuild -us -uc

```

There is also useful information on building debian packages here: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

