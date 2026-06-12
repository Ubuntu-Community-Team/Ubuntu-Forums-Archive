---
title: "Compiling a 32-bit C++ app on 64-bit Kubuntu"
date: 2011-02-09
forum: Packaging and Compiling Programs
---

### Post by daihard on 2011-02-09
Hi.

I am trying to compile a C++ application on 64-bit Kubuntu 10.10. The compilation went smoothly (using "-m32" with gcc), but the linker complained as follows.

```
g++ -m32 -g  -shared  -o librdmecppapi10.so   Cursor.o  Db.o  DbTypes.o  ICursor.o  IDb.o -L/home/dtoyama/rdme/centralia/lib/lnx/ -lrdmerdm10 -lrdmebase10 -lrdmepsp10 )
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libstdc++.a when searching for -lstdc++
```

Apparently the linker does not know where to look for the 32-bit version of the C++ library. I do have libstdc++ under /usr/lib32. The same process on a 32-bit C program works just fine, just the C++ components fail as above.

Anyone have any idea what I am missing here? Thanks!

---

### Post by MadCow108 on 2011-02-10
do you have g++-multilib installed?

---

