---
title: "Undefined reference to `memcpy@GLIBC_2.14' : Building Android SDK with SmartCard API"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by arttykh on 2013-11-12
I am trying to build Android emulator with SmartCard API support.
I was following this manuals: [[one]("http://source.android.com/source/building.html")] [[two]("https://code.google.com/p/seek-for-android/wiki/EmulatorExtension")]

All steps passed ok, but when I run:
```
PCSC_INCPATH=<path_to_pcsc-lite_32bit>/src/PCSC/ PCSC32_LIBPATH=<path_to_pcsc-lite_32bit>/src/.libs/ PCSC64_LIBPATH=<path_to_pcsc-lite_64bit>/src/.libs/ make -j32 PRODUCT-sdk-sdk
```

I have got the following error:
```
make: *** [out/host/linux-x86/obj/EXECUTABLES/emulator64-arm_intermediates/emulator64-arm] Error 1
/<my-home>/pcsc-lite-1.8.10_x64/src/.libs//libpcsclite.so: undefined reference to `memcpy@GLIBC_2.14'
```

My glib version is **2.15**:
```
ldd --version
ldd (Ubuntu EGLIBC 2.15-0ubuntu10.5) 2.15
```

How can I solve this issue? Should I downgrade glibc to version 2.14 or there is any other solution?

**OS**: Ubuntu 12.04 x64

---

### Post by Shivam_Kumar on 2014-03-25
Hey were you able to resolve the issue... I am facing the same problem

---

