---
title: "I need GCC 4.8 in Ubuntu 12.04"
date: 2013-03-17
forum: Repositories &amp; Backports
---

### Post by Shiryu on 2013-03-17
I have GCC 4.6 in Ubuntu 12.04 (Precise).
I need GCC 4.8 because it has new C++11 features and I have to keep 12.04 because it is LTS.

How to update GCC?

---

### Post by james_mcl on 2013-08-09
I think all the information you need should be at:

[https://launchpad.net/~ubuntu-toolchain-r/+archive/test/](https://launchpad.net/~ubuntu-toolchain-r/+archive/test/)
[https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)

It's not absolutely perfect when compiling with -g though. gcc 4.8 apparently uses a new version of the format for the debugging symbols by default, which doesn't match what the Precise Pangolin version of gdb is expecting. There's no later version of gdb in this repository, so you have to compile with -g -gdwarf-2 for compatibility. See [http://gcc.gnu.org/gcc-4.8/changes.html](http://gcc.gnu.org/gcc-4.8/changes.html) for the details.

(I'm actually currently trying to find a repository with a later version in. Because I don't know what this gdb-minimal in later versions of Ubuntu is, though, I'll probably end up installing the version at [https://www.gnu.org/software/gdb/](https://www.gnu.org/software/gdb/))

---

