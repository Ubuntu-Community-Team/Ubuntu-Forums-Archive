---
title: "problems with openembedded"
date: 2009-05-08
forum: Programming Talk
---

### Post by uglyoldbob on 2009-05-08
There are problems compiling with openembedded using ubuntu 8.10, 9.04 (possibly others).
Problems exist when compiling dbus-1.0.1 and linux-2.6.21 as the versions for the sources when compiling.
dbus/dbus/dbus-sysdeps-unix.c has problems with not having struc ucred defined. The fix is to edit the source file after it is unpacked by maunally adding in the definition of this structure. The problem here is that you have to do this modification every time you recompile.
linux/scripts/mod/sumversion.c needs to have #include <limits.h> added to it. I don't remember the exact method of failure here.
I am looking for a cleaner method of getting this stuff to work.

This is covered here ([http://www.gumstix.net/wiki/index.php?title=Build_Environment_Ubuntu_9.04](http://www.gumstix.net/wiki/index.php?title=Build_Environment_Ubuntu_9.04)) which explains a way to get it to work, but is at best a hack.

---

