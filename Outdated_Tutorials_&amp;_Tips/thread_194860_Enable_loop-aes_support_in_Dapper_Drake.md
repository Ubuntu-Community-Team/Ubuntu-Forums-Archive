---
title: "Enable loop-aes support in Dapper Drake"
date: 2006-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Stephen Robertson on 2006-06-12
To support loop-aes encryption, you need to download and install the loop-aes-source and loop-aes-utils packages.  After installing both packages, use the following steps to enable loop-aes support:

1.  Open a terminal window.
2.  Type *cd /usr/src*
3.  Unpack the loop-aes source tarball.  Type *sudo tar xvjf loop-aes.tar.bz2*
4.  There is a bug in the loop-aes package that must be fixed before the loop-aes
     package can be built.  Type *cd modules/loop-aes/debian* .
5.  Type *sudo chmod a+x rules*
6.  Type *cd /usr/src*
7.  Now, you need to repack the loop-aes tarball to include the modification you
     just made.  Type *sudo rm loop-aes.tar.bz2*
8.  Type *sudo tar cvf loop-aes.tar  modules/loop-aes*
9.  Type *sudo bzip2 loop-aes.tar*
10.  Now, you can build the loop-aes package.  Type *sudo m-a fakesource*
11.  Type *sudo m-a build loop-aes*
12.  Finally, type *sudo dpkg -i loop-aes-<your package version>.deb* to
       install the loop-aes kernel modules.  You can now use loop-aes to encrypt
       your hard drive partitions.

---

### Post by lex1 on 2006-06-12
Steve,

thanks for info on loop-aes if you have time maybe you have time howto
encrypt home or root?

lex1;)

---

### Post by Fab on 2006-06-12
if this works, you are my new hero ;P

edit: and it does! many thanks for this one! :) :)

---

