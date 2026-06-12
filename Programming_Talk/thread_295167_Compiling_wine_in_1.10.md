---
title: "Compiling wine in 1.10"
date: 2006-11-07
forum: Programming Talk
---

### Post by WhiteDawn on 2006-11-07
Hi,
Ok, straight to the problem...
I have never had trouble compiling wine on Ubuntu 1.06, but for some reason it just isn't working on 1.10. All dependencies have been fulfilled, and ./configure completes perfectly. make depend && make also completes without errors, but when i type make check i get this

```

make[1]: Entering directory `/home/whitedawn/Desktop/wine-0.9.24/tools'
make[1]: `makedep' is up to date.
make[1]: Leaving directory `/home/whitedawn/Desktop/wine-0.9.24/tools'
make[1]: Entering directory `/home/whitedawn/Desktop/wine-0.9.24/dlls'
make[2]: Entering directory `/home/whitedawn/Desktop/wine-0.9.24/dlls/advapi32/tests'
../../../tools/runtest -q -P wine -M advapi32.dll -T ../../.. -p advapi32_test.exe.so crypt.c && touch crypt.ok
Segmentation fault (core dumped)
make[2]: *** [crypt.ok] Error 139
make[2]: Leaving directory `/home/whitedawn/Desktop/wine-0.9.24/dlls/advapi32/tests'
make[1]: *** [advapi32/tests/__test__] Error 2
make[1]: Leaving directory `/home/whitedawn/Desktop/wine-0.9.24/dlls'
make: *** [dlls/__test__] Error 2

```

any help?

---

### Post by WhiteDawn on 2006-11-07
sorry for bumping, but is there anyway to view the core dump?

After searching a bit I found out that advapi32 is related to openssl. Sadly I cannot remove it because apt-get thinks it is corrupted, and apt-get wont install it because it is installed allready.

I tryed runing a package of 0.9.22 and it installed and ran perfectly. Strangely, for some reason it will not run xfire (a chat program made for windows). The strange part is that xfire ran automagicly on ubuntu 1.6 with the same virsion of wine...

---

### Post by WhiteDawn on 2006-11-07
Om, sorry for bothering you... but i fixed my problem!

all i had to do is run ./configure CFLAGS=-fno-stack-protector instead of just ./configure

---

