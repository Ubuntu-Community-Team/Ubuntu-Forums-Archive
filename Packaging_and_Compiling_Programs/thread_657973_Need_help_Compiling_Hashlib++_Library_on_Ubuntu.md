---
title: "Need help: Compiling Hashlib++ Library on Ubuntu"
date: 2008-01-04
forum: Packaging and Compiling Programs
---

### Post by one-up on 2008-01-04
Hello, I am trying to compile the Hashlib++ Library on Ubuntu.
I have G++ and the buildessentials installed.
When I read the readme file it first tells me to extract the archive.
I CD to the directory i've downloaded the tar.gz to, and type tar xvfz hashlib2plus_0.2_src.tar.gz
It just extracts al the files to hashlib++_0.2, no errors.
I CD to that directory, and then to the src directory, and type make.
It gives the following output:
g++ -c hl_md5.cpp
g++ -c hl_md5wrapper.cpp
g++ -c hl_sha1.cpp
g++ -c hl_sha1wrapper.cpp
g++ -c hl_sha256.cpp
g++ -c hl_sha256wrapper.cpp
ar rs libhl++.a hl_md5.o hl_md5wrapper.o hl_sha1.o hl_sha1wrapper.o hl_sha256.o hl_sha256wrapper.o
ar: creating libhl++.a
Everything goes fine until now, the readme file tells me to type make install.
I get the following output:
ar rs libhl++.a hl_md5.o hl_md5wrapper.o hl_sha1.o hl_sha1wrapper.o hl_sha256.o hl_sha256wrapper.o
cp libhl++.a /usr/local/lib/ &&
/bin/sh: Syntax error: end of file unexpected
make: *** [install] Error 2
Why do I get this error message, it does not work because I cannot compile the example projects included.

---

### Post by one-up on 2008-01-05
Anyone please?

---

### Post by public_void on 2008-01-05
Are you running make install as sudo, because make install copies files to /usr/local/*, so requires root permissions.

---

### Post by one-up on 2008-01-06
I tried to run sudo make install, but I get the same errors.

---

