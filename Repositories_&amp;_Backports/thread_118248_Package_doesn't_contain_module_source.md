---
title: "Package doesn't contain module source"
date: 2006-01-16
forum: Repositories &amp; Backports
---

### Post by hwinkler on 2006-01-16
Hi all,

I am looking for the sources for the atmel at76c503 drivers.

I used dpkg to locate the package for the module:

dpkg --search at76c503.ko 

(lsmod indicates that module is loaded) and dpkg says that file is in the kernel package linux-image-2.6.12-10-386.

So then I did

apt-get source linux-image-2.6.12-10-386

but those sources do not contain the source code for the module (looking for at76c503.c, among others).

Can someone please point me in the right direction to get this source correctly? Thanks!

Hugh

---

