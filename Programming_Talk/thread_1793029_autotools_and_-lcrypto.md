---
title: "autotools and -lcrypto"
date: 2011-06-28
forum: Programming Talk
---

### Post by fsleeman on 2011-06-28
I am working on a project with a preexisting autotool configure/Makefile systems that compiles a number of source files into a library. Right now, I am trying to add some code to use the MD5 checksum from the openssl library (-lcrypto) but without any success.I have read a lot of examples online but nothing I have found quite works.

In my case, I need my code to compile on Linux and Solaris. I have been able to link the crypto library on Linux but not Solaris. The openssl location is not the standard path so I needed to added a --with-crypto=path. I was able to add that parameter and was able to verify that I was setting AM_LDFLAGS, LIBS, etc. as I expected in the configure.ac file but when I used the AM_CHECK_LIB it couldn't find it. Does anybody know that needs to be set for the Makefiles to find the library?

All I need to do is the determine if the openssl library is found (allowing for a user specified path), and if so link it.

---

