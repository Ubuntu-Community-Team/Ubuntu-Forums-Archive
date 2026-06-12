---
title: "Man does not support c programming"
date: 2005-04-23
forum: Programming Talk
---

### Post by sbm on 2005-04-23
Hi

I have installed GCC-33 on my ubuntu system.
I've chosen gcc-docs aswell.
My problem is how to setup man to enable me to for instance do a:
man 2 dup
man open

etc.

Hope anyone can help
I'm normally a java programmer, so hacking a bit of c on the linux kernel is a new world to me :-), but extremely interesting.....

/SBM

---

### Post by nad on 2005-04-23
Man is not a kernel internel. Your first source of information should be the manual page, ' man man '.

In order to modify man, you will need the source code available at packages.debian.org.

Have fun

Dan M

---

### Post by dcraven on 2005-04-23
```
sudo apt-get install glibc-doc
```

---

### Post by vague- on 2005-04-26
See also "manpages-dev", probably the package you are looking for.

```

$ apt-cache show manpages-dev
[...]
Description: Manual pages about using GNU/Linux for development
 These man pages describe the Linux programming interface, including
 these two sections:
 2 = Linux system calls.
 3 = Library calls (note that a more comprehensive source of information
     may be found in the glibc-doc package).
[...]

```

Notice that it mentions the aforementioned "glibc-doc", however.

---

### Post by bfelisberto on 2007-01-10
In Edgy glibc docs are split into glibc-doc and glibc-doc-reference.
As of today glibc-doc-reference conflicts with glibc-doc. If you have the glibc-doc package installed you need to completely remove it to install glibc-doc-reference and vice-versa.

---

### Post by abjorne on 2007-02-25
[QUOTE=vague-;148379]See also "manpages-dev", probably the package you are looking for.

[...]

I installed manpages-dev and the manpages I needed are now available (thanks a lot);
I tried to install glibc-doc but I got the following:

```

# apt-get install -f glibc-doc
[...]
Unpacking glibc-doc (from .../glibc-doc_2.4-1ubuntu12.3_all.deb) ...
dpkg: error processing /var/cache/apt/archives/glibc-doc_2.4-1ubuntu12.3_all.deb (--unpack):
 trying to overwrite `/usr/share/doc-base/glibc-manual', which is also in package glibc-doc-reference
Errors were encountered while processing:
 /var/cache/apt/archives/glibc-doc_2.4-1ubuntu12.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

what am I supposed to do?

Thanks

---

