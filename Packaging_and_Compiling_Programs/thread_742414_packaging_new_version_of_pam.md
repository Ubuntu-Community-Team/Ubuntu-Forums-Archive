---
title: "packaging new version of pam"
date: 2008-04-01
forum: Packaging and Compiling Programs
---

### Post by NiN on 2008-04-01
Hi there!  I have the following problem:  I want to package a new version of pam, which supports sha256 and sha512 hash algorithms in it's configuration in combination with glibc 2.7.  The problem is, that the debian / ubuntu version is heavily patched and a vanilla source does not work with eighter debian / ubuntu (tested with sid and hardy)  Does someone know which patches are absolutely necessary to allow authentication? I only want a version, that can authenticate against the default configuration (local password auth), but with hashes other than md5.  Any help apreciated!

---

