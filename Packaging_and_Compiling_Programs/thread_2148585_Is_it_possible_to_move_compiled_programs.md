---
title: "Is it possible to move compiled programs ?"
date: 2013-05-25
forum: Packaging and Compiling Programs
---

### Post by mozartripper on 2013-05-25
Is it possible to compile lets say apache on my workstation then move it to my server ?

---

### Post by ohnonot on 2013-05-26
what would you copy/move? are you talking about creating a .deb file?

that might be possible.

---

### Post by mozartripper on 2013-05-30
No i'm not creating a deb file. I'm doing ./configure, make, make install. I want to know if after doing make install I can transfer the compiled files to another machine. As I don't want to install all the packages needed to compile on the server machine.

---

### Post by steeldriver on 2013-05-30
provided the target machine has the same architecture as the build machine, and has any shared libraries that the program requires

---

### Post by ohnonot on 2013-05-31
yes,> **steeldriver said:**
> provided the target machine has the same architecture as the build machine, and has any shared libraries that the program requires
...and it doesn't conflict with sth already installed on the other machine.

---

