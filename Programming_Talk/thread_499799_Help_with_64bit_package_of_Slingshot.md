---
title: "Help with 64bit package of Slingshot"
date: 2007-07-13
forum: Programming Talk
---

### Post by musther on 2007-07-13
Don't know if you saw the thread I posted about Slingshot:
[http://ubuntuforums.org/showthread.php?t=492797](http://ubuntuforums.org/showthread.php?t=492797)

Anyway, it's a game, currently written in python.

Now, we have a 32 bit .deb which people have been using on Ubuntu.  Some people wanted to play on 64 bit so forced the package (it's python, so no problem).  But there was a bug which only appeared on 64 bit versions.

So, now we've fixed the bug, and we'd like to make a .deb (and preferably a .rpm) for 64 bit users.  I asked a member of the forums to build one for me using epm (I don't have access to a 64 bit machine).  So he built me a .deb on his amd64 machine, and then tried to install it, but got this:

```
    dpkg: error processing slingshot-0.8p.deb (--install):
     package architecture (x86_64) does not match system (amd64)
    Errors were encountered while processing:
     slingshot-0.8p.deb
```

So obviously his machine is amd64, so how the package came out x86_64 I don't know.  

Are there different 64 bit architectures, and if so do we need to make a package for each?

The package to use when making distributable packages is:
[http://musther.googlepages.com/Slingshot-buildpack-x64.tar.gz](http://musther.googlepages.com/Slingshot-buildpack-x64.tar.gz)
It has instructions for using epm to make .deb and .rpm packages.  All information (dependencies, website, description, files) is in the file slingshot.list, ready for epm.

---

### Post by kidders on 2007-07-14
Hi there,

I have a 64-bit box, but (at least with Ubuntu), it always thinks of itself as x86_64, rather than amd64 ... even though it *is* an AMD64. The distinction is a little like i386 vs i686 in the 32-bit world ... the architecture names refer to specific CPU instruction sets that a package may want to use.

You'll notice at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) that Ubuntu adopts a pretty generic approach to CPU architectures. It doesn't make much of an attempt to distinguish between Sempron & Celeron chips, for instance, and just calls them all "i386". Similarly, I would suggest configuring your 64-bit package for x86_64, rather than amd64. I wonder if the guy who tested your package has customised (ie more tightly optimised) his system. I'd offer to test it myself, but my 64-bit box no longer has Ubuntu on it. :-(

People seem to *love* you game! I must try it. :-)

---

