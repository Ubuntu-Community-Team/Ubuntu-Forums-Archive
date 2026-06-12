---
title: "Compiling from source code - make install error 126"
date: 2012-03-27
forum: Packaging and Compiling Programs
---

### Post by spiralciric on 2012-03-27
Ok, I did as root ./configure, make and on make install I get the image attached. F1?

---

### Post by raja.genupula on 2012-03-27
Hi you have to run make install with sudo (i mean as a root .)
so change to root and continue . but please post the text , dont attach the image . 

     thank you .:)

---

### Post by spiralciric on 2012-03-27
Off course I did run make install as root, that can be seen on image (other than the # sign, for regular users, they have @ sign before and color is green, for root color is red). You are right, I should have posted text instead of image:
```
eee-virtual-machine lxlauncher-0.1.6-jemimah-puppy-menu-patches # make install
Making install in src
make[1]: Entering directory `/home/eee/lxlauncher-0.1.6-jemimah-puppy-menu-patches/src'
make[2]: Entering directory `/home/eee/lxlauncher-0.1.6-jemimah-puppy-menu-patches/src'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'lxlauncher' '/usr/local/bin/lxlauncher'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/eee/lxlauncher-0.1.6-jemimah-puppy-menu-patches/src'
make[1]: Leaving directory `/home/eee/lxlauncher-0.1.6-jemimah-puppy-menu-patches/src'
Making install in po
make[1]: Entering directory `/home/eee/lxlauncher-0.1.6-jemimah-puppy-menu-patches/po'
if test -r ".././mkinstalldirs"; then \
      .././mkinstalldirs /usr/local/share; \
    else \
      /bin/sh ../mkinstalldirs /usr/local/share; \
    fi
/bin/sh: .././mkinstalldirs: Permission denied
make[1]: *** [install-data-yes] Error 126
make[1]: Leaving directory `/home/eee/lxlauncher-0.1.6-jemimah-puppy-menu-patches/po'
make: *** [install-recursive] Error 1

```

---

### Post by oldos2er on 2012-03-27
Thread moved to Packaging and Compiling Programs.

---

