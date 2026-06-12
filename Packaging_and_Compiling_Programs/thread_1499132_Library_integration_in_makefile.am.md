---
title: "Library integration in makefile.am"
date: 2010-06-01
forum: Packaging and Compiling Programs
---

### Post by Zohair08 on 2010-06-01
Hello everyone,

I am writing a matlab library (*.so )and using it in c++ code. The library depends on some .h headers located at DIRECTORY1 and some .so libraries located at DIRECTORY2. I am writing a makefile.am file and I read that I should use LDFLAGS and LIBADD with -rpath and -L but really didn't understand what exactly I should do. any explanation and help please?

Cheers
Zoh

---

### Post by SevenMachines on 2010-06-08
you should have a look though [this quick libtool guide]("http://www.ensta.fr/%7Ediam/dev/online/autoconf/autobook/autobook_92.html") which has a bit of an explanation on how to use LIBADD and LDADD in makefile.am and see if its any help, if you're still having some problems, post some code too if you can

---

