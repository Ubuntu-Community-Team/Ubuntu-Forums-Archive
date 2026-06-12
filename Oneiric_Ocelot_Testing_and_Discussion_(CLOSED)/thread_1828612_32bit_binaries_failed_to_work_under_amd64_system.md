---
title: "32bit binaries failed to work under amd64 system"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by portis on 2011-08-19
After a recent upgrade of ia32-libs, 32bit programs, such as skype, wine etc no longer work under amd64 system.

$file /usr/bin/skype
/usr/bin/skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped

$ ldd /usr/bin/skype
	not a dynamic executable

Bug rerpot: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/829309](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/829309)

---

### Post by dino99 on 2011-08-19
Less trouble with 32 bits PAE kernel

---

### Post by Bowmore on 2011-08-19
This is due to the transition of ia32-libs into multiarch.
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-August/000886.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2011-August/000886.html)

The goal is to phase out ia32-libs and I guess this transiston will break some 32-bit applications temporarilly on its way for those running 64-bit Ubuntu.

---

### Post by portis on 2011-08-19
Quite strange. I thought it is a loader problem, so I
downgrade libc6 as well as libc6-i386 and then upgrade to the current version. Now 32bit programs can be loaded.
And I can install missing i386 multiarch packages.

---

