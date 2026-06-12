---
title: "libcurl c header file"
date: 2009-02-01
forum: Programming Talk
---

### Post by smarmo on 2009-02-01
I have a c program that uses "curl.h" that I'm trying to compile on intrepid ibex server edition. I've compiled the program before on mac os x by using "#include <curl/curl.h>", compiling with "gcc -lcurl mysource.c -o myexecutable", and it works perfectly. But on ubuntu, I get "error: curl/curl.h: No such file or directory." Here are my questions:

Does ubuntu already have that file and I just need to find it?
Is there a package I need to install? If so, what? And once I install the package, where does it put the "curl.h" file?
Is it possible to simply download the "curl.h" file from somewhere, put it in the correct directory, and it will work?

Any help is greatly appreciated.

---

### Post by smarmo on 2009-02-01
I forgot to mention that I have successfully compiled other c programs that only use "stdio.h" and/or "math.h".

---

### Post by smarmo on 2009-02-01
SOLUTION:

I needed the "libcurl4-gnutls-dev" package. It works now.

---

### Post by jespdj on 2009-02-02
Most libraries in Ubuntu come with a corresponding **lib...-dev** package, so if you're writing a program that uses a certain library, look for the -dev package for that library and install it.

---

