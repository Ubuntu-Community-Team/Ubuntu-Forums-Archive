---
title: "Dependency not satisfiable: libcdio-cdda0"
date: 2010-09-29
forum: Packaging and Compiling Programs
---

### Post by skepticalgeek on 2010-09-29
I have created a fairly sophisticated Qt app using Qt Creator. It compiles and runs just fine on my development PC. I am trying to create a simple binary package for deployment testing. I used ldd to determine the dependencies for my program, and included them in the control file. I have created the deb package just fine. When I move it to my deployment machine and double-click on it, or even double-click on it on the development machine, GDebi gives me a dependency not satisfiable error for libcdio-cdda0. I looked in Ubuntu Software Center, and that library is listed there and it says it is installed. I did not include version info in any of my depends, so it is not a version conflict. How is it not able to resolve a dependency for a library that it has installed? 

Sorry if this is a dumb question. I am new to Linux development. I have experience with Windows packaging tools like Inno and Install Shield, but this is my first try at trying to package and deploy a Linux app. Also, is there any command I can run that will examine the deb file, and list all the dependency errors, so I can solve them all, rather than just one at a time? Thanks.

Patrick Ferre aka skepticalgeek

---

### Post by Bachstelze on 2010-09-29
Try to install your package with

```
sudo dpkg -i foo.deb
```

And paste the whole output.

---

### Post by skepticalgeek on 2010-09-29
Here is the command, and the output. This is from the development machine.

patrick@patrick-laptop:~/SKG_Jukebox$ sudo dpkg -i skg-jukebox_0.7_all.deb > z.txt
dpkg: dependency problems prevent configuration of skg-jukebox:
 skg-jukebox depends on libcdio_cdda0; however:
  Package libcdio_cdda0 is not installed.
 skg-jukebox depends on libcdio_paranoia0; however:
  Package libcdio_paranoia0 is not installed.
 skg-jukebox depends on libqtxml4; however:
  Package libqtxml4 is not installed.
 skg-jukebox depends on libqtnetwork4; however:
  Package libqtnetwork4 is not installed.
 skg-jukebox depends on libpthread0; however:
  Package libpthread0 is not installed.
 skg-jukebox depends on libm6; however:
  Package libm6 is not installed.
 skg-jukebox depends on libgcc_s1; however:
  Package libgcc_s1 is not installed.
 skg-jukebox depends on libvorbis0; however:
  Package libvorbis0 is not installed.
 skg-jukebox depends on librt1; however:
  Package librt1 is not installed.
 skg-jukebox depends on libdl2; however:
  Package libdl2 is not installed.
 skg-jukebox depends on libsolid4; however:
  Package libsolid4 is not installed.
 skg-jukebox depends on libkdecore5; however:
  Package libkdecore5 is not installed.
 skg-jukebox depends on libqtdbus4; however:
  Package libqtdbus4 is not installed.
 skg-jukebox depends on libkde3support4; however:
  Package libkde3support4 is not installed.
 skg-jukebox depends on libmusicbrainz4; however:
  Package libmusicbrainz4 is not installed.
 skg-jukebox depends on libkio5; however:
  Package libkio5 is not installed.
 skg-jukebox depends on libkdeui5; however:
  Package libkdeui5 is not installed.
 skg-jukebox depends on libqt3support4; however:
  Package libqt3support4 is not installed.
 skg-jukebox depends on libglib-2.00; however:
  Package libglib-2.00 is not installed.
 skg-jukebox depends on libpng120; however:
  Package libpng120 is not installed.
 skg-jukebox depends on libgobject-2.00; however:
  Package libgobject-2.00 is not installed.
 skg-jukebox depends on libx116; however:
  Package libx116 is not installed.
 skg-jukebox depends on libgthread-2.00; however:
  Package libgthread-2.00 is not installed.
 skg-jukebox depends on ld-linux2; however:
  Package ld-linux2 is not installed.
 skg-jukebox depends on libbz20; however:
  Package libbz20 is not installed.
 skg-jukebox depends on libkparts4; however:
  Package libkparts4 is not installed.
 skg-jukebox depends on libkpty4; however:
  Package libkpty4 is not installed.
 skg-jukebox depends on libqtsvg4; however:
  Package libqtsvg4 is not installed.
 skg-jukebox depends on libqtsql4; however:
  Package libqtsql4 is not installed.
 skg-jukebox depends on libutil1; however:
  Package libutil1 is not installed.
 skg-jukebox depends on libxml22; however:
  Package libxml22 is not installed.
dpkg: error processing skg-jukebox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skg-jukebox


SO basically, nearly all my depends are listed as not installed, despite the fact that I used them to create the app. Clues anyone?

---

### Post by Bachstelze on 2010-09-29
The package is libcdio-cdda0, not libcdio_cdda0. As a general rule, there are no underscores in package names.

---

### Post by skepticalgeek on 2010-09-30
I changed the underscores to hyphens, in libcdio-cdda and libcdio-paranoia. I also got rid of or renamed some of the dependencies that dpkg was complaining about. This is now my situation: if I try to open the package with GDebi, it complains that the libFlac++6 dependency is not satisfiable, and stops. If I install it with dpkg -i, it seems to install everything, but complains there were errors, but it doesn't elaborate. I need to read the man page to see if there is a verbose switch, that will tell me more. This is all happening on the development machine. I haven't tried it on the target machine yet. 

BTW, are the library names in the depends section of the control file case sensitive? In the control files of some other deb packages I have looked at, the library names are all lowercase. Is this a standard I should be adhering to? Thanks for the help so far.

Patrick Ferre aka skepticalgeek

---

### Post by Bachstelze on 2010-09-30
> **skepticalgeek said:**
> 
BTW, are the library names in the depends section of the control file case sensitive?

Those are actually the names of the packages tht contain the libraries, not the name of the libraries themselves. That being said, yes, they are case-sensitive (pretty much everything in Linux is).

> Is this a standard I should be adhering to?

Yes. The Debian Policy, section 5.6.1, states:

> Package names (both source and binary, see Package, Section 5.6.7) must consist only of lower case letters (a-z), digits (0-9), plus (+) and minus (-) signs, and periods (.). They must be at least two characters long and must start with an alphanumeric character. 

It is technically possible to have uppercase letters if you really need to, but you probably don't.

---

### Post by skepticalgeek on 2010-10-01
Thanks for the help. I've got a deb package now hat GDebi can open without complaining about dependencies. Now to just deploy it on the target machine, and see what happens.

---

