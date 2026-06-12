---
title: "trying to compile libvisual-plugins"
date: 2005-12-04
forum: Packaging and Compiling Programs
---

### Post by Kimm on 2005-12-04
I'm trying to compile libvisual-plugins so that I can try out the aeon music player.
I successfully compiled libvisual but libvisual-plugins is bugging me, it claims that the X11 headers is missing while it is most defenently there.

```
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking X11/keysym.h usability... no
checking X11/keysym.h presence... no
checking for X11/keysym.h... no
configure: error: Required X11 headers not found.

```

Could anyone help me? or perhaps provide me with a link to a precompiled package?

---

### Post by Kimm on 2005-12-04
No mather, I fixed it.

I found the library libvisual0.2-plugins at debian and installing that made everything better.

Ps.
In case anyone else has the same problem, download libvisual0.2-plugins from debian and install it, after that, search for actor_geforce.so at rpm.pbone.net, after you find it, download the package and salvage that file, then copy it to /usr/lib/libvisual/actor/actor_geforce.so. It will be missing if you dont.

---

