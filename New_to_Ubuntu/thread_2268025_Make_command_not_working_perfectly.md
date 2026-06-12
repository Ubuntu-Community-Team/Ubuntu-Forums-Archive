---
title: "Make command not working perfectly"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by Raman_Butta on 2015-03-05
I am new to Ubuntu and have tried to install a number of Softwares from their source tar.gz packages. I've found that in many cases, the 'make' command generates error while building the package. Is it the fault in the source code itself, or is this command not a general one for installing all tar-zipped softwares ?

---

### Post by Holger_Gehrke on 2015-03-05
No, 'make' is **one** tool for controlling compilation and  linking - basically turning source code into an executable binary file.  There's several others, for example ant (used mostly for java), or  makefile-generators like qmake, cmake or automake. 

If 'make' fails, it's usually not a problem with the source code but a problem with your system, specifically missing libraries and header files. Nobody puts all the libraries his program uses into a tarball. There's usually a text-file accompanying the source code stating what libraries are needed. You need to install these before compiling. You need the developer files for the libraries, those are found in the repositories in files named just like the libraries themselves but with the suffix '-dev'. Those contain the header files and pull in the libraries through dependencies.

Often there's a script named 'configure' in the root directory of the source tree. It examines your system and tells you what libraries you're missing. It can also be used to set various options for the package you're building, calling it with the option '--help' wil tell you what options are available.

---

