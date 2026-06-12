---
title: "cross compiling issue"
date: 2008-09-16
forum: Packaging and Compiling Programs
---

### Post by Kouran-sama on 2008-09-16
hi im trying to cross compile a program for an embedded arm-linux platform. i have the sourcecode and tried the following command:
```

CC=arm-linux-gcc ./configure --host=arm-linux --build=i686-linux --prefix=/home/kora/Desktop/Gumstix/trunk/build_arm_nofpu/root

```
i need the prefix directory since the file system image is build upon this directory. 
This is the output:
```

Serching in .
Found .
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /home/kora/Desktop/dtnperf/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for arm-linux-strip... no
checking for strip... strip
configure: WARNING: In the future, Autoconf will not detect cross-tools
whose name does not start with the host triplet.  If you think this
configuration is useful to you, please write to autoconf@gnu.org.
checking for arm-linux-gcc... arm-linux-gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

```
Configure cant find the arm-linux-strip. Can i get this program somewhere and if yes, would i have to place it into the prefix directory or is this just needed for compiling?

Thanks in advance for any hints
tom

---

### Post by NoReflex on 2008-09-16
Maybe I'm wrong but ... try to run the command as root. As far as I can see the **C compiler cannot create executables**. Or you can check the file permissions.

Best wishes,
NoReflex

---

### Post by Kouran-sama on 2008-09-16
i did run the command as root so there should be no problem with writing files. im trying to find a package that has the arm-linux-strip inside, but i havent found one yet.

thanks
tom

---

