---
title: "Anyone know this C COde"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by tak.neha on 2008-10-17
I have to write a code C for malloc function it does the same work as original...can anyone have any idea abt this...plz send me the code:confused:

---

### Post by panhandle on 2008-10-17
Your post is confusing. Try here:

[http://en.wikipedia.org/wiki/Malloc](http://en.wikipedia.org/wiki/Malloc)

---

### Post by niteshifter on 2008-10-17
Hi,

Er, get the source(s) from the repos?

First, make a folder in your home folder to put them in and change to it:
```
mkdir test
cd test

```
Next get the sources for libc6. It's big - about 17MB to download:
```
apt-get source libc6
```

What you're after is in the folder glibc-2.6.1 in your test folder:
```
cd glibc-2.6.1
```
Which will have several archive files. You want the archive glibc-2.6.1.tar.bz2, so open it with the gui file roller app. You want this folder - _within the archive_:
/glibc-2.6.1/malloc

There you will find malloc.c

---

