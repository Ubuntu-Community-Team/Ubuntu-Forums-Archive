---
title: "Make error when installing Accountability Pal"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by koopa184 on 2014-09-14
I'm trying to install a URL-logging software called Accountability Pal, but the installation instructions don't seem to be working.

Its first instructions:
"1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package."

I've cd'd to the directory and configured it, but when I type make, the terminal responds with

make: *** No targets specified and no makefile found.  Stop.

I'm new to Linux (first time using it today), so I'm not sure exactly how to remedy the error.

---

### Post by Impavidus on 2014-09-15
First, manually compiling and installing software is about the last thing to try when we install software on Ubuntu (the only thing less convenient being writing the software yourself). We prefer installing stuff from the software centre using the Ubuntu repositories, or PPAs or stand-alone .deb's. Are you sure this software or an alternative that you can use too are not available via these channels?

Then, it seems you don't have a makefile. The makefile is usually created by the configure script. Which raises the question, did the configure script return any errors? They often do and the thing to do then is often installing the development version of some library, which comes with a bunch of header files.

---

### Post by Vladlenin5000 on 2014-09-15
You do realize that your software hasn't been updated since a decade ago?

---

