---
title: "installing perl modules not in repository"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by fedoraboy on 2008-09-01
I am a ubuntu beginner, but long time unix user.

I have a new hardy ubuntu server and am trying to fold some needed perl libraries into it.

I thought i could do:
sudo dh-make-perl --install --cpan Example::Module

This does the normal cpan fetching.  But when it then builds the module in / (yes, I mean the root directory).  Then, when it goes to install it, it cannot find it.

I can do:
dh-make-perl --build --cpan Example::Module # i.e. build as me
sudo dpkg install libexample-module-perl

... so I am working fine.  I just feel like I am missing something obvious.  (Environment variable?)  I have tried re-initializing cpan, but I am beginning to think it is in the package manager stuff.

---

### Post by diamantis13 on 2008-10-09
I think this might help you:
[CPAN on Ubuntu fails on bug IO/Uncompress/RawInflate.pm: solution ]("http://nxadm.wordpress.com/2008/05/30/cpan-on-ubuntu-fails-on-bug-iouncompressrawinflatepm-solution/")

---

