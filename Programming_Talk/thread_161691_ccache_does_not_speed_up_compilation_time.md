---
title: "ccache does not speed up compilation time"
date: 2006-04-17
forum: Programming Talk
---

### Post by MichaelZ on 2006-04-17
Hello,

I would like to use ccache (compiler cache) to speed up the compilation of C++ applications.

ccache was already installed on my system (even if I do not remember if I did it or was installed by default). Anyway, I have followed the instruction reported in *man ccache* and chosen  to use the symbolic links (*ln -s*).

Now I have the .ccache on my home directory:

/home/michael/.ccache

Unfortunately it seems that the ccache is not really used and the compilation time of C++ programs is the same (or quite). For example, the creation of a .deb package takes 90 minutes. With the ccache just 1 or 2 minutes less.

Did I something wrong or do I miss something?

Thank you very much.

Best wishes,
Michael

---

### Post by toojays on 2006-04-17
ccache only speeds up the compilation of programs which you have already compiled, and only when you are recompiling with the same compiler and compiler options.

What deb package takes 90 minutes to build?

---

### Post by MichaelZ on 2006-04-18
Hello,

Thank you very much for your reply.

Yes, I know that ccache only speeds up the compilation of programs which you have already compiled.

What I want is to speed up the building of a deb package for [CodeBlocks]("http://www.codeblocks.org"). Building this package takes me 90 minutes, because my desktop is relatively old (PIII 500MHz, 500MB).

Anyway, each re-building takes me the approximately the same amount of time.

A FC4 user has told me to install the ccache in the root account, but Ubuntu has not really a root account (it could, but it seem not wise).

Best wishes,
Michael

---

### Post by toojays on 2006-04-19
It sounds like the debian/rules file could be ignoring your PATH, which means that it isn't using ccache at all. Does it go faster if you manually run make, rather than using dpkg-buildpackage?

---

### Post by MichaelZ on 2006-04-19
[quote=toojays]It sounds like the debian/rules file could be ignoring your PATH, which means that it isn't using ccache at all. Does it go faster if you manually run make, rather than using dpkg-buildpackage?[/quote] 
I think not, but I do not use make a lot at this point. To build my programs I use the built-in system of [CodeBlocks]("http://www.codeblocks.org"). Anyway, it should speed up the building of any program using gcc/g++/cc (so I have understood from man ccache). But the building is still slow as before.

I have checked to know which g++ was used with the command which and I get as answer: /usr/local/bin/g++

This should be correct as my ln is:

ln -s /usr/local/bin/ccache /usr/local/bin/g++

Anyway, the ccache is used, but I have just 2 files cached instead of 800-1000 files (what a FC4 user told me, even if he has .ccache in the root account).

Strange:-k.

Best wishes,
Michael

---

