---
title: "Adding to pkg-config search path"
date: 2010-03-12
forum: Programming Talk
---

### Post by y50a7XpWRH66IV on 2010-03-12
Hi all,

I am currently writing a program that will utilise libtar to manipulate some tar files.

I have installed libtar and libtar-dev from the repository.

When compiling my program in kdevelop, pkg-config complains that libtar is not in its search path. The header file, however is in usr/includes.

How do I go about adding libtar to the pkg-config search path?

Thanks :)

---

### Post by dwhitney67 on 2010-03-12
Typically, /usr/share/pkgconfig is where the pkg-config files reside.

For specific information on how to setup a pkg-config "pc" file, reference the manpage for pkg-config.  A good example is provided.

---

