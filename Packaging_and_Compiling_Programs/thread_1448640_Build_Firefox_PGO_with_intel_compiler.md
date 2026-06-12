---
title: "Build Firefox PGO with intel compiler"
date: 2010-04-06
forum: Packaging and Compiling Programs
---

### Post by mononom on 2010-04-06
Hello.

I tried to build firefox 3.7a4 with PGO using intel compiler, but received following error messages.

```
../../dist/include/mozilla/mozalloc.h(220): error: exception specification is incompatible with that of previous function "operator new(size_t={unsigned long})" (declared at line 91 of "/usr/include/c++/4.4.1/new"):
            previously specified but omitted here: "std::bad_alloc"
  void* operator new(size_t size) MOZALLOC_THROW_BAD_ALLOC
                                  ^

../../dist/include/mozilla/mozalloc.h(232): error: exception specification is incompatible with that of previous function "operator new[](size_t={unsigned long})" (declared at line 92 of "/usr/include/c++/4.4.1/new"):
            previously specified but omitted here: "std::bad_alloc"
  void* operator new[](size_t size) MOZALLOC_THROW_BAD_ALLOC
```

My .mozconfig file is...
```

. $topsrcdir/browser/config/mozconfig

export CC=icc
export CXX=icc
export LD=xild
export AR=xiar
mk_add_options AUTOCONF=autoconf2.13

ac_add_options --enable-application=browser
mk_add_options MOZ_CO_PROJECT=browser
mk_add_options MOZ_MAKE_FLAGS=-j2
mk_add_options MOZ_OBJDIR=/home/mono/src/obj-PGO-intel-@CONFIG_GUESS@
#mk_add_options PROFILE_GEN_SCRIPT=/home/mono/src/run-firefox.sh

ac_add_options --enable-optimize="-O3 -xSSE3 -funroll-loops -finline-functions -static -pipe -fomit-frame-pointer"
ac_add_options --disable-debug
ac_add_options --disable-tests
ac_add_options --enable-gnomeui
#ac_add_options --enable-profile-guided-optimization
ac_add_options --disable-crashreporter
ac_add_options --enable-safe-browsing
ac_add_options --enable-faststart
ac_add_options --disable-necko-wifi
```

And, when i compiled it using gcc, there's no error, but, compiling PGO using gcc, I got the segmentation fault. 

What can i do?
Please let me know that what to do to compile using icc and what made a problem of compiling PGO using gcc..

My system is...
Intel C2Q 6600
Gigabyte P35-DS3R
2GB DDR2
Nvidia 8500GT



sorry for poor english.

Ubuntu 9.10 Karmic.
Intel C Compiler 11.1

---

