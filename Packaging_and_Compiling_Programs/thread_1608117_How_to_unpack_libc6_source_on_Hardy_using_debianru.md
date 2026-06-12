---
title: "How to unpack libc6 source on Hardy using debian/rules?"
date: 2010-10-28
forum: Packaging and Compiling Programs
---

### Post by nutznboltz on 2010-10-28
How do I unpack the libc6 source code on Hardy without building everything?

I run
```
apt-get source libc6
```
and I get
```
$ ls -1d glibc-2.7/*
glibc-2.7/debian
glibc-2.7/glibc-2.7.tar.bz2
glibc-2.7/glibc-libidn-2.7.tar.bz2
glibc-2.7/glibc-linuxthreads-20071023.tar.bz2
glibc-2.7/glibc-ports-2.7.tar.bz2
glibc-2.7/stamp-dir
```

What I want is the unpacked and patched source code.

Using google find this lovely blog:
[http://lizardo.wordpress.com/2008/05/31/setting-up-libc6-sources-for-analysis-on-debianubuntu/](http://lizardo.wordpress.com/2008/05/31/setting-up-libc6-sources-for-analysis-on-debianubuntu/)
Which says to run:
> ./debian/rules configure_i686


But all I get is
```
$ ./debian/rules configure_i686
make: *** No rule to make target `configure_i686'.  Stop.
```
Besides I want to unpack for amd64 (x86_64) not i686 anyway.

So what is the super-secret target for unpacking libc6 via debian/rules?

I don't have the space to use the build target, I just want to unpack the source code and patch it for examination.

---

### Post by nutznboltz on 2010-10-28
well

```
debian/rules unpack
```

unarchived the tarballs.

Not sure yet about patches.

---

### Post by nutznboltz on 2010-10-28
```
$ ~/src/libc6/glibc-2.7$ ./debian/rules patch
Applying patches...successful.
```

[GWNMF]("http://www.google.com/search?q=libc6+%22debian%2Frules+patch%22")

---

