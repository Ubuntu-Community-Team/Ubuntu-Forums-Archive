---
title: "How to cross arch compile on the PPA build system?"
date: 2014-03-13
forum: Packaging and Compiling Programs
---

### Post by yeled-nova on 2014-03-13
Hello,

I made a software for Linux, both x86 and x64. The software uses several 32bit commerical binaries which I don't have sources. Therefore, in order to work with these close-sourced binaries, some of my code needs to be compiled to 32bit as well (LD_PRELOAD magic).

The software itself has no problem to compile/package. (It works on Arch User Repo, and on my local Ubuntu 13.10 x86 & x64). Now I am thinking to publish my software via the PPA.

Here's related sections in debian/control.
[COLOR=#0000cd]Build-Depends:
 gcc [i386], gcc-multilib [amd64],
 libglib2.0-dev [i386], libglib2.0-dev:i386 [amd64],
 pkg-config [i386], pkg-config:i386 [amd64],
 debhelper (>= 9), ...

Package: ....
Architecture: i386 amd64
[/COLOR]

The problem is, amd64 build fails, complaining
...
[COLOR=#0000cd]libglib2.0-dev:i386: missing
libglib2.0-dev:i386: does not exist
...
pkg-config:i386: missing
pkg-config:i386: does not exist[/COLOR]
...
Does the PPA build system not understand the ":i386" flag? If not, what should I do to enable the cross architecture compiling?


Thanks in advance.

---

