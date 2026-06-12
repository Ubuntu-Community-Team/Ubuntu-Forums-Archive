---
title: "Using gcc 4.7 in Ubuntu 12.04 ?"
date: 2012-08-24
forum: Programming Talk
---

### Post by prismctg on 2012-08-24
How to use gcc 4.7 in ubuntu 12.04 and how to make it default ?

---

### Post by Bachstelze on 2012-08-24
If you have to ask, the answer is you can't. Upgrade your OS.

---

### Post by angryfirelord on 2012-08-24
Is there a compelling reason to use a newer gcc? (aside from having a higher version number)

---

### Post by MadCow108 on 2012-08-24
4.7 has a bunch of neat features, to name a few:
transactional memory support
better c++11 and C11 support
__builtin_assume_aligned and many improvements to the autovectorizer

there are usually backports of gccs available in ppa's
e.g. the official toolchain testbuild ppa contains gcc4.7 for precise:
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test/+packages](https://launchpad.net/~ubuntu-toolchain-r/+archive/test/+packages)

in the past that worked very well for me, though the last time I used it was when gcc 4.5 was new

---

