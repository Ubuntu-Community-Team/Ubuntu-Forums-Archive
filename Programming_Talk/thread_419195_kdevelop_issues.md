---
title: "kdevelop issues"
date: 2007-04-22
forum: Programming Talk
---

### Post by rbprogrammer on 2007-04-22
ok, so i create a new c/c++ hello world project, but no matter what i have as code, i always get the same error:
```
cd '/media/disk/development/test' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && cd '/media/disk/development/test/debug' && CXXFLAGS="-O0 -g3" "/media/disk/development/test/configure" --enable-debug=full && cd '/media/disk/development/test/debug/./src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k test
aclocal
autoheader
automake
autoconf
/bin/sh: /media/disk/development/test/configure: Permission denied
*** Exited with status: 126 ***

```
not sure what else to post here...

but what could be not allowing me to have permission? kdevelop had enough permission to create the project with all of its files and directories.  

i didnt have this problem before when i had dapper.  i just recently (as in a few hours ago) installed feisty fawn.  which by the way is SO-WEET!

any help would be appreciated...

---

### Post by rbprogrammer on 2007-04-26
bump

---

### Post by tylerevans on 2007-05-13
I had the same problem and solved it by adding the 'exec' mount option in fstab for the partition that the project was being stored in.

---

