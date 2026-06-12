---
title: "Compiling GMP on Ubuntu 10.04 with Code::Blocks"
date: 2010-12-29
forum: Packaging and Compiling Programs
---

### Post by nebkat on 2010-12-29
Can someone give me a step by step guide for compiling GMP on Ubuntu 10.04? Im going to be making an app in c++ with Code::Blocks and I am going to need extra functions of GMP. 

I have already tried compiling with Code::Blocks but I got about 50 errors. I think my problem is about where I put the files I downloaded from GMP. 

After an update my system got corrupted so I had to reinstall Ubuntu and now it is an absolutely fresh install.

---

### Post by SevenMachines on 2010-12-30
Unless you explicitly need the absolutely latest version of gmp, install the repository version
$ sudo apt-get install libgmp3-dev

If you especially want to compile it from source (are you really, really sure:) ) then you are best not using codeblocks or an ide and in the source directory run ./configure and make and see if you get any errors then

---

### Post by MadCow108 on 2010-12-30
before compiling yourself do:
apt-get build-dep libgmp3-dev

this is likely to install all dependencies for building gmp

---

