---
title: "necessary libraries of c,c++,java"
date: 2008-04-09
forum: Programming Talk
---

### Post by haha123 on 2008-04-09
hello guys ... are all the necessary libraries for c,c++,java got installed with ubuntu?i have libc6.if these libraries are not installed by default  somebody tell me where to get them?

---

### Post by themusicwave on 2008-04-09
I don't know what you consider necessary, it really depends what libraries you need.

I think a package called build essential contains most of the common c/c++ libraries.

For Java I know you need to install the Sun JDK.  I forget the exact package name and am not at my Ubuntu box.  In Synaptic search for Java.  It should be something like Sun-JDK6 or something like that.

---

### Post by ibutho on 2008-04-09
For the C/C++ development files, you need to install the build-essential package. As for java, install sun-java6-jdk.

---

### Post by Zugzwang on 2008-04-09
If installing programs using the package manager, all the libraries needed for these programs are automatically installed with the programs.

If you want to program your own stuff, then what's necessary depends on what you need. Try "sudo apt-get install build-essential" if you're using C/C++ or "sudo apt-get install sun-java6-jdk" if you want to program Java. These commands will install all the *basic* libraries & tools for compiling your own programs. The other libraries you *might* need (e.g. for GUI) have to be installed separately since the system can't guess what you need.

---

