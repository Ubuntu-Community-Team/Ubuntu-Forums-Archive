---
title: "aclocal trouble"
date: 2006-08-27
forum: Programming Talk
---

### Post by artifex on 2006-08-27
I'm using an Ubuntu 6.06.1 (updating time to time started from 'Ubuntu-Server 6.04 "Dapper Drake" - Alpha i386 (20060218)') on x86.

I've been trying compile libtorrent and had problems with pkg-config. I found that I have /usr/share/aclocal and /usr/share/aclocal-1.9 folders. I have automake1.9 installed but pkg-config install its pkg.m4 in aclocal (as many other packages as well).

Why packages install files in aclocal if aclocal-1.9 exist? Why aclocal is not a symlink to aclocal-1.9? Of course I copied all files from aclocal to aclocal-1.9 and make aclocal as symlink to aclocal-1.9 so I am able to compile libtorrent but I'm looking for a clean solution.

---

