---
title: "Ubuntu &quot;-dev&quot; libraries packages not actually including any library"
date: 2015-05-06
forum: Packaging and Compiling Programs
---

### Post by Webanck on 2015-05-06
Hello, I am currently trying to compile a program on Ubuntu 15.04.
Before that I was compiling it successfully on ubuntu 14.04 but it was requiring some libraries like the libmagick++-dev one for instance.
The thing is, trying to install all those libraries packages is very painful on vivid.
Indeed, I can't find any ".so" file corresponding to the library and nor does the compiler ;(.

Am I completely dumb or is it because it is relatively new? A "-dev" package should include a ".so or .a" file right?

---

### Post by steeldriver on 2015-05-06
Hello and welcome to the forums

A -dev package doesn't necessarily contain .so (or .a) libraries - sometimes they just contain the required header files, while the library files are provided by the corresponding runtime package. Additionally, some -dev packages don't contain much at all, and just refer to the current package via their dependencies e.g. for Vivid, the libmagick++-dev package appears to depend on libmagick++-6.q16-dev, which is the package that actually contains the libraries.

You may find [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to be useful - I also find the apt-file utility helpful for resolving this kind of thing

---

