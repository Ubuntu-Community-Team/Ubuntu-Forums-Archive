---
title: "building 32-bit app to run on 64-bit system"
date: 2009-02-27
forum: Packaging and Compiling Programs
---

### Post by kornelix on 2009-02-27
I am trying to build a 32-bit application to run on Jaunty 64-bit. I think this can be done, but I am having a build problem I don't understand. I am using g++ with the -m32 option to build a 32-bit executable. Here is the output of the linker:

mico@mico1:~/Desktop/fotoxx$ make -B
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.3/../../../libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: cannot find -lgtk-x11-2.0
collect2: ld returned 1 exit status
make: *** [fotoxx] Error 1

I gave up trying to find libgtk-x11-2.0 (32 bit version). Does it exist? Am I trying to do something that cannot be done?

---

### Post by nzadLithium on 2009-03-02
there is a program called getlibs. You can use that to install 32bit libraries like this:

getlibs -l libraryname.so

It may be able to find the libs you want (its found nearly all of the ones I wanted :D).

---

### Post by kornelix on 2009-03-05
Thanks, I will try it out.

---

