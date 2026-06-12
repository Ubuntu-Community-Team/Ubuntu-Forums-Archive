---
title: "Make .deb from binary file"
date: 2010-02-23
forum: Packaging and Compiling Programs
---

### Post by yanom on 2010-02-23
I have a program that is contained in a single binary file, Fusion.
Typing

$ ./Fusion

starts the program. It depends on GTK. It's a freeware but non-FOSS program. Is there anyway i can make a .deb from just this binary?

---

### Post by Bachstelze on 2010-02-24
Are you familiar with creating DEBs for packages built from source? If so, just create a Makefile for it with an install rule that will copy the binary in place, and proceed as usual with the debian/* files.

---

### Post by gmargo on 2010-02-24
You just need a directory structure and a DEBIAN/control file. This sticky thread from the Programming-Talk forum has the info: 

'How to make a "Basic" .deb' [http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

---

### Post by yanom on 2010-02-24
Thankyou, thats helpful

---

