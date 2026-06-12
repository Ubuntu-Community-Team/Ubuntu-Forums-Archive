---
title: "Compile kernel driver x86 on x64 OS error"
date: 2015-07-31
forum: Packaging and Compiling Programs
---

### Post by vezinadj on 2015-07-31
I am currently attempting to compile a kernel driver for x86 on a x64 ubuntu 14.04 using autotools ./configure, make, make install. Here are the steps I have taken:

1. Installed build-essential, g++-multilib and gcc-multilib
2. ./configure --build=i686-pc-linux-gnu "CFLAGS=-m32" "CXXFLAGS=-m32" "CPPFLAGS=-m32" "LDFLAGS=-m32"
3. make all
4. sudo make install

step 4 and it is giving me this error:

/usr/bin/ld: i386:x86-64 architecture of input file `...' is incompatible with i386 output (... is one of the .o build file names)

I am not sure what I am missing. Any one have any ideas I could try?

---

