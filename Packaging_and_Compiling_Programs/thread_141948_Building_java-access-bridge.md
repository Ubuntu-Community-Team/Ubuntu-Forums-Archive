---
title: "Building java-access-bridge"
date: 2006-03-09
forum: Packaging and Compiling Programs
---

### Post by rw615 on 2006-03-09
Greetings,

I am trying to build some assistive technology in Java and want to use the java-access-bridge.  It appears that I need to build and install it from source.  When I run ./configure, however, I get this error:

$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... found
checking for "/home/rick/apps/jdk1.5.0_06/bin/java"... yes
checking JDK version... 1.5.0
checking for "/home/rick/apps/jdk1.5.0_06/bin/javac"... yes
checking for "/home/rick/apps/jdk1.5.0_06/bin/idlj"... yes
checking for "/home/rick/apps/jdk1.5.0_06/bin/jar"... yes
checking for pkg-config... /usr/bin/pkg-config
checking for bonobo-activation-2.0 libspi-1.0 >= 1.7.0... Package bonobo-activation-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `bonobo-activation-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'bonobo-activation-2.0' found
configure: error: Library requirements (bonobo-activation-2.0 libspi-1.0 >= 1.7.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I installed the build-essential package and the bonobo, bonobo-activation and, for the heck of it, bonobo-conf packages.

I do not find a bonobo-activation.pc file on my machine.  My default pkg-config directories are apparently /usr/lib/pkgconfig and /usr/share/pkgconfig

Any thoughts?

---

### Post by hod139 on 2006-03-09
try installing the libbonobo2-dev package

---

### Post by apfreire on 2008-03-05
The libspi-1.0 library is installed with the package libatspi-dev.

After installing bonobo as suggested above, try:

sudo apt-get install libatspi-dev

---

