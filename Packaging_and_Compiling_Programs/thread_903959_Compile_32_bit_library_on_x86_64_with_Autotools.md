---
title: "Compile 32 bit library on x86_64 with Autotools"
date: 2008-08-28
forum: Packaging and Compiling Programs
---

### Post by nomexous on 2008-08-28
I'm writing a program on my 64-bit machine which is intended to be compiled and copied over to a 32 bit machine. (Copying over the source code and compiling it on the 32-bit machine is not an option.) In the Makefile, I have a "32" section which adds a -m32 flag to g++'s compile line.

E.g.:```
32: this.o that.o
     g++ -m32 this.o that.o -o binary
```
I then run "make 32" which builds the 32-bit version which I will copy over. During compilation, g++ will search for the 32-bit libraries to link. Using getlibs, I can satisfy the commonly used 32-bit dependencies (libcurl and libxml2) but run into problems with a package that I needed to compile. I didn't install libconfig from the repositories. Instead, I downloaded the source, ./configure-ed, make-ed, and sudo make install-ed.

Of course, this only got me the 64-bit library. What I need is to get the library in 32-bit (without overwriting the 64-bit version) so I can properly do a "make 32". Is there a way to do this during the ./configure stage of building libconfig? Like "./configure -32bit"?

---

### Post by skullmunky on 2008-09-16
I tried to do this a while back and the most reliable ways I could find were either fakeroot or, my favorite solution, putting 32 bit on another partition.

---

### Post by spideylinux on 2008-10-07
Just wanted to let you know that I was able to use the -m32 option.  But to get the correct libraries I went to Synaptic search for "g++ multilib" and you should see a package with the latest g++ available.  Choose to install it an it's dependencies. Worked like a charm for me.

---

