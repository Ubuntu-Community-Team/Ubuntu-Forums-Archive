---
title: "can i get an explanation please?"
date: 2010-04-15
forum: Programming Talk
---

### Post by daweefolk on 2010-04-15
Hi I'm trying to make a LFS system (yes, i know these are ubuntu forums, lol) and I want to set it up so i have my own system setup (/apps rather than /bin, /users rather than /home and so on) and the symlinks in the LFS book are confusing me. I guess symlinks are a wee bit beyond my knowledge ATM. Can someone explain how I would change this code to replace /bin with /apps when i'm building my system?
```
ln -sv /tools/bin/{bash,cat,echo,pwd,stty} /bin
ln -sv /tools/bin/perl /usr/bin
ln -sv /tools/lib/libgcc_s.so{,.1} /usr/lib
ln -sv /tools/lib/libstdc++.so{,.6} /usr/lib
ln -sv bash /bin/sh
``` 
An explanation of what a symlink is and how they work (just imagine you're writing a 'for dummies' book) would be much much appreciated

Oh, and if this is the wrong forum to post into, sorry. I didn't see where else to put it as it isn't really ubuntu-related

---

### Post by CptPicard on 2010-04-15
Symlinks are just aliases for a file that resides somewhere else on the filesystem. They sort of "point" to the "real" file.

But about your project... you're asking for trouble IMO for no gain. Especially when building LFS, your builds will assume certain standard directories, and even when running, applications are likely to get confused.

There are more worthy configuration endeavours than just renaming stuff that everyone expects to be called some certain way :)

---

### Post by Bachstelze on 2010-04-16
What Captain said. ;) Also, no offense meant but if symlinks are above your head, I don't think LFS is quite fit for you. It can be a good learning experience, but it has some prerequisites, I suggest you try Gentoo first, or even a debootsrapped Ubuntu.

---

