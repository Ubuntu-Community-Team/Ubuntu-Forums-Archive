---
title: "gcj: libgcj.spec: No such file or directory"
date: 2009-01-07
forum: Programming Talk
---

### Post by gimpmaster3201 on 2009-01-07
I am trying to install GNU GCJ ([http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)) on Ubuntu

I did this using the command: 

```
sudo apt-get install gcj
```


The problem is that when I try to use it I get an error. The command I use:

```
gcj
```

The error I get:

gcj: libgcj.spec: No such file or directory


The version I am using: 

```
gcj -dumpversion
```

4.2.4


I have this file in the directory /usr/lib/gcc/i486-linux-gnu/4.1
I copied it to /usr/lib/gcj.4.2-8.1
But it didn't seem to make a difference.

Can any one with this problem?
I have looked into this and I cannot find much about it.
Any help will be very appreciated.

Ash

---

### Post by jespdj on 2009-01-07
What do you want to use gcj for, why do you want to install it?

Sun Java works much better. GNU Java is an incomplete and very slow version of Java 1.4.2, which, as far as I know, is not being developed anymore because Sun Java is becoming open source.

Maybe you want to use gcj to compile your Java code to native code. Note that that will not make your Java program run much faster than when you use Sun Java. Sun Java contains a very sophisticated JIT (just-in-time) compiler which compiles your Java bytecode to native code on the fly.

---

### Post by gimpmaster3201 on 2009-01-07
Hi


It is not my choice to use this compiler, I use Suns compiler for my Java code as you suggested.

The reason I need the gcj compiler to work is because I am trying to install LibxmlJ ([http://www.gnu.org/software/classpathx/jaxp/apidoc/gnu/xml/libxmlj/transform/package-summary.html]("http://www.gnu.org/software/classpathx/jaxp/apidoc/gnu/xml/libxmlj/transform/package-summary.html")). 
This is a Java API the uses the C library libxml2 ([http://xmlsoft.org/]("http://xmlsoft.org/")) This is a parsing toolkit for XML.

When I try to install LibxmlJ using ./configure I get this error for gcj

```

...
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... gcj: libgcj.spec: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for gcj... gcj -C
checking if gcj -C works... configure: error: The Java compiler gcj -C failed (see config.log, check the CLASSPATH?)

```


Part of the config.log

```

...
configure:17315: checking if gcj supports -fno-rtti -fno-exceptions
configure:17348: result: no
configure:17363: checking for gcj option to produce PIC
configure:17550: result: -fPIC
configure:17558: checking if gcj PIC flag -fPIC works
configure:17576: gcj -c -I/usr/include/libxml2 -g -O2 -I/usr/include/libxml2  -fPIC conftest.java >&5
gcj: libgcj.spec: No such file or directory
configure:17580: $? = 1
configure:17591: result: no
configure:17615: checking if gcj supports -c -o file.o
configure:17636: gcj -c -I/usr/include/libxml2 -g -O2 -I/usr/include/libxml2  -o out/conftest2.o conftest.java >&5
gcj: libgcj.spec: No such file or directory
configure:17640: $? = 1
configure:17660: result: no
configure:17686: checking whether the gcj linker (/usr/bin/ld) supports shared libraries
configure:18535: result: yes
configure:18606: checking dynamic linker characteristics
configure:19146: result: GNU/Linux ld.so
configure:19150: checking how to hardcode library paths into programs
configure:19175: result: immediate
configure:19189: checking whether stripping libraries is possible
configure:19194: result: yes
configure:20942: checking for gcj
configure:20958: found /usr/bin/gcj
configure:20968: result: gcj -C
configure:21025: checking if gcj -C works
configure:21039: gcj -C  Test.java
gcj: error trying to exec 'ecj1': execvp: No such file or directory
configure:21042: $? = 1
configure:21046: error: The Java compiler gcj -C failed (see config.log, check the CLASSPATH?)

```


If I ignore this and I proceed to use the make command if get this error:

```

...
javah -jni -classpath classes gnu.xml.libxmlj.dom.GnomeXPathNSResolver
javah -jni -classpath classes gnu.xml.libxmlj.dom.GnomeXPathResult
source='source/javax/xml/datatype/DatatypeConfigurationException.java' object='source/javax/xml/datatype/DatatypeConfigurationException.lo' libtool=yes \
        DEPDIR=.deps depmode=none /bin/bash ./config/depcomp \
        /bin/bash ./libtool --mode=compile --tag=GCJ gcj -fjni -fassume-compiled -I./source -g -O2 -c -o source/javax/xml/datatype/DatatypeConfigurationException.lo `test -f 'source/javax/xml/datatype/DatatypeConfigurationException.java' || echo './'`source/javax/xml/datatype/DatatypeConfigurationException.java
 gcj -fjni -fassume-compiled -I./source -g -O2 -c source/javax/xml/datatype/DatatypeConfigurationException.java
gcj: libgcj.spec: No such file or directory
make[1]: *** [source/javax/xml/datatype/DatatypeConfigurationException.lo] Error 1
make[1]: Leaving directory `/home/ashley/programs/LibxmlJ/jaxp-1.3'
make: *** [all] Error 2

```

This uses the gcj compiler which is why i need it to work. 
Has anyone else tried to install LibxmlJ? Do you have any suggestions?

Ash

---

### Post by jespdj on 2009-01-08
Do you absolutely need that library to parse XML in Java? There are better options available. Since Java 1.4, Java has a built-in XML parser in the standard library, lookup the docs for the package javax.xml.parsers.

I searched on [http://packages.ubuntu.com](http://packages.ubuntu.com) for [packages containing the file libgcj.spec](http://packages.ubuntu.com/search?searchon=contents&keywords=libgcj.spec&mode=exactfilename&suite=intrepid&arch=any). You probably need to install the package libgcj8-dev or libgcj9-dev.

---

### Post by gimpmaster3201 on 2009-01-08
Yes I need to use this library to parse my input files. I have used others in the past but using libxml2 is a requirement in this instance.

I have installed libgcj8-dev, libtool, ecj, eclipse, gdb. As i thought some of them might give some insight to the problem. 

I have access to a machine running Fedora and the gcj command works fine on that, its just getting it to work on Ubuntu is such a nightmare.

---

