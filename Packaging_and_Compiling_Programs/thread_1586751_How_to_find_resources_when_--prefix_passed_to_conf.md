---
title: "How to find resources when --prefix passed to configure"
date: 2010-10-02
forum: Packaging and Compiling Programs
---

### Post by JupiterV2 on 2010-10-02
When a user uses the --prefix, --datadir, etc flags to change where resources may be installed to (rather than the default /usr/local), how do you find/access these from within C. It seems the most obvious answer would be to use something like AC_SUBSTR(["DATA_DIR"], @datadir@) but the few configure.ac files I've looked at, and their resulting config.h files, don't seem to use this method.

How is this done?

---

### Post by SevenMachines on 2010-10-03
You might want to look at 
[http://www.gnu.org/software/hello/manual/autoconf/Defining-Directories.html#Defining-Directories](http://www.gnu.org/software/hello/manual/autoconf/Defining-Directories.html#Defining-Directories)

Undoubtedly a better explanation than i could manage :)

---

### Post by JupiterV2 on 2010-10-04
Thanks, this is what I was looking for..

---

