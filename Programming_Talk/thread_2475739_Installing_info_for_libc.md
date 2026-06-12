---
title: "Installing info for libc"
date: 2022-06-07
forum: Programming Talk
---

### Post by sundaresh on 2022-06-07
info pages for libc is not installed on my ubuntu hirusite-hippo . How do I install it ?

---

### Post by spjackson on 2022-06-07
You probably need the glibc-doc-reference package.

---

### Post by sundaresh on 2022-06-07
Would ,

$ apt install glibc-doc-reference

do it ?

---

### Post by TheFu on 2022-06-07
Why not try and see what happens?

---

### Post by guiverc on 2022-06-07
Be aware that Ubuntu 21.04 and all *flavors* are [B]*end-of-life*.
[/B]
[URL="https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/"]https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/

[/URL]> **Ubuntu 21.04 (Hirsute Hippo) End of Life reached on January 20 2022**
As of January 20, 2022, Ubuntu 21.04 is no longer supported. No more  package updates will be accepted to 21.04, and it will be archived to  old-releases.ubuntu.com in the coming weeks.
[URL="https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/"]

[/URL]Also be aware that the [warning has already gone out for Ubuntu 21.10's EOL]("https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/"), as once that reaches EOL you'll lose your upgrade path without re-install.  Ubuntu 21.04 (*hirsute hipp**o*) was **not** a LTS release, thus it's QA-tested & *supported* upgrade path is to the next release, which is gone when it's EOL.

---

### Post by TheFu on 2022-06-08
+1.

Definitely don't bother with 21.04 at this point.  I wouldn't bother with 21.10 either.  The choices are 22.04 or 20.04, both are LTS releases.
I don't keep up with code names.  Use release numbers and confusion is removed completely.

---

