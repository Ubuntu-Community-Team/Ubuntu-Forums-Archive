---
title: "CMake fails to find Java on PPA"
date: 2010-08-12
forum: Packaging and Compiling Programs
---

### Post by Serguey Basalaev on 2010-08-12
I'm training in packaging and trying to create a set of packages for a simple library. Library is written in C with bindings to Java and build system is CMake. CMake uses command FIND_PACKAGE(Java) to find Java and when I build a package on my PC all builds normally. But when I try it on PPA CMake is unable to find Java no matter what. I'm pretty sure that all dependencies are set. Isn't it the same CMake as on my PC?
You can get sources by executing:
$ dget https://launchpad.net/~sbasalaev/+archive/pub/+files/libhello_0bzr7-0pub2_source.changes

---

### Post by SevenMachines on 2010-08-12
> dh_install: libhello-java missing files (usr/share/java/*), aborting
make: *** [binary-install/libhello-java] Error 2
Its not a java problem judging by the buildlog, looks like you're trying to install to a directory that doesnt exist on a default install with the dependencies you have, try adding

debian/libhello-java.dirs:
> usr/share/java

---

### Post by SevenMachines on 2010-08-12
Ignore that last post, thats not the problem

---

### Post by SevenMachines on 2010-08-12
It does seem to be a cmake problem, maverick will build fine with the newer version of cmake but lucid won't. I'm not sure the best way to pass/patch it so that java is found.

---

### Post by Serguey Basalaev on 2010-08-13
Oh, I see. I use cmake from lucid-backports. I guess I just put updated CMake packages in my PPA to build with them.

---

### Post by SevenMachines on 2010-08-13
I've only got maverick here but i get the problem using a downgraded cmake from lucid on it and its fine with cmake from maverick so i'm assuming thats the issue, the java module for cmake seems to have changed fairly significantly between the 2 versions. Theres maybe some options that can be passed to get it building with the lucid version but i really dont know enough about cmake. An updated cmake ppa version should work.... i think

---

### Post by Serguey Basalaev on 2010-08-17
It works! Thanks for help

---

### Post by SevenMachines on 2010-08-17
good stuff. you might want to file a bug on cmake if it isnt finding java with default-jre.

---

