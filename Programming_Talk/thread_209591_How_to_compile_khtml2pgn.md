---
title: "How to compile khtml2pgn??"
date: 2006-07-05
forum: Programming Talk
---

### Post by johann_p on 2006-07-05
I try to compile khtml2png ([http://khtml2png.sourceforge.net/)](http://khtml2png.sourceforge.net/)).
But when I run configure I get the following error message:

WARNING: This project requires version: 2.4.0 of cmake.
You are running version: 2.23
CMake Error: KDE3_DIR is not set.  It must be set to the directory containing KDE3Config.cmake in order to use KDE3.

I have installed the kde-devel (universe) but that does not seem to be sufficient.
Any ideas?

---

### Post by Note360 on 2006-07-05
do you have gcc? That could cause the problem.

---

### Post by johann_p on 2006-07-05
[quote=Note360]do you have gcc? That could cause the problem.[/quote]

Yep --  gcc/g++ 4.0.3 and lots of other development packages are installed.

---

### Post by johann_p on 2006-07-05
Addon-question: would such a conflict between essential packages qualify as an (K)Ubuntu bug? And is there a chance that such a bug would get corrected?
I really need both the kde-devel AND the kdesvn packages quite desperately ... :/

---

### Post by RichardBanks on 2006-07-18
> **johann_p said:**
> Addon-question: would such a conflict between essential packages qualify as an (K)Ubuntu bug? And is there a chance that such a bug would get corrected?
I really need both the kde-devel AND the kdesvn packages quite desperately ... :/

The kdesvn conflict comes from Debian. It seems that kde-devel will replace kdesvn in time IMO.

As for the khtml2png the version of cmake is too old.

I downloaded the binary (tar.gz) package from the [cmake](http://www.cmake.org/) website and changed the configure script to point to the downloaded file.

---

### Post by johann_p on 2006-07-18
> **RichardBanks said:**
> The kdesvn conflict comes from Debian. It seems that kde-devel will replace kdesvn in time IMO.

As for the khtml2png the version of cmake is too old.

I downloaded the binary (tar.gz) package from the [cmake]("http://www.cmake.org/") website and changed the configure script to point to the downloaded file.

Thanks -- it seems that indeed the cmake package is too old :(

As for kdesvn, I really feel this is a bug, no matter whose fault it is. After all I can't use botch packages at the same time in Ubuntu and that is not good in rather unpleasant way. :neutral:

So is it to be expected that at some point that conflict will be resolved in an update or what is somebody to do who wants both conflicting packages?

---

