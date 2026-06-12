---
title: "problems with automake and configure in KDevelop"
date: 2007-06-04
forum: Programming Talk
---

### Post by ishaqmalik on 2007-06-04
When I try to build a project in KDevelop, it says:

There is no Make file in this directory and no configure script for this project, Run automake and friends and configure first?

When I click "Run Then", it outputs the following error in the messages window:

```
cd '/home/ishaq/test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/ishaq/test/debug' && cd '/home/ishaq/test/debug' && CXXFLAGS="-O0 -g3" "/home/ishaq/test/configure" --enable-debug=full && cd '/home/ishaq/test/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

```

Does this mean I don't have the mentioned programs installed, if yes, how can I install them. 

(I had installed KDevelop through "Add/Remove" in the Applications menu, didn't it install automake and configure)

Regards,
MI

---

### Post by GeneralZod on 2007-06-04
Hi, 

See [http://ubuntuforums.org/showthread.php?t=460227](http://ubuntuforums.org/showthread.php?t=460227), especially the HOWTO linked by Daller.

Hope this helps!

---

### Post by ishaqmalik on 2007-06-05
Thanks General :)

    KDevelop works fine now, but if I open Documentation tab, it tries to go online, is it possible to download the documentation to my hdd for easy reference offline?

Regards,
MI

---

