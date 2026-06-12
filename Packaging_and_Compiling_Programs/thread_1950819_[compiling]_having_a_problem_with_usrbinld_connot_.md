---
title: "[compiling] having a problem with /usr/bin/ld connot find -lz"
date: 2012-04-01
forum: Packaging and Compiling Programs
---

### Post by RainerZA on 2012-04-01
Hi, I am currently trying to build android 4.0.4 for the first time, but i'm having some problem while building c++ files.

when I try to run "make-j4" from [Android compiling instructions]("http://source.android.com/source/building.html") so I run "make -j1" to check where the error occurs and I get this.

```
============================================
PLATFORM_VERSION_CODENAME=AOSP
PLATFORM_VERSION=4.0.4.0.4.0.4
TARGET_PRODUCT=full
TARGET_BUILD_VARIANT=eng
TARGET_BUILD_TYPE=release
TARGET_BUILD_APPS=
TARGET_ARCH=arm
TARGET_ARCH_VARIANT=armv7-a
HOST_ARCH=x86
HOST_OS=linux
HOST_OS_EXTRA=Linux-3.0.0-17-generic-x86_64-with-Ubuntu-11.10-oneiric
HOST_BUILD_TYPE=release
BUILD_ID=OPENMASTER
OUT_DIR=out
============================================
host Executable: aapt (out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/aapt)
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/aapt] Error 1

```

i'm guessing i'm missing some libraries or links for it to miss "/usr/bin/ld: cannot find -lz"

running Ubuntu 11.10 64-bit

Thanks for any help in advance :D

---

### Post by oldos2er on 2012-04-01
Moved to Packaging and Compiling Programs.

---

### Post by idoitprone on 2012-04-01
> **RainerZA said:**
> Hi, I am currently trying to build android 4.0.4 for the first time, but i'm having some problem while building c++ files.

when I try to run "make-j4" from [Android compiling instructions]("http://source.android.com/source/building.html") so I run "make -j1" to check where the error occurs and I get this.

```
============================================
PLATFORM_VERSION_CODENAME=AOSP
PLATFORM_VERSION=4.0.4.0.4.0.4
TARGET_PRODUCT=full
TARGET_BUILD_VARIANT=eng
TARGET_BUILD_TYPE=release
TARGET_BUILD_APPS=
TARGET_ARCH=arm
TARGET_ARCH_VARIANT=armv7-a
HOST_ARCH=x86
HOST_OS=linux
HOST_OS_EXTRA=Linux-3.0.0-17-generic-x86_64-with-Ubuntu-11.10-oneiric
HOST_BUILD_TYPE=release
BUILD_ID=OPENMASTER
OUT_DIR=out
============================================
host Executable: aapt (out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/aapt)
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make: *** [out/host/linux-x86/obj/EXECUTABLES/aapt_intermediates/aapt] Error 1

```i'm guessing i'm missing some libraries or links for it to miss "/usr/bin/ld: cannot find -lz"

running Ubuntu 11.10 64-bit

Thanks for any help in advance :D



did you follow these directions?
[http://source.android.com/source/initializing.html](http://source.android.com/source/initializing.html)[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

### Post by SevenMachines on 2012-04-01
Especially note that on amd64 you still require the x86 version of zlib
```
$ sudo apt-get install zlib1g-dev:i386
```

---

### Post by RainerZA on 2012-04-01
> **SevenMachines said:**
> Especially note that on amd64 you still require the x86 version of zlib
```
$ sudo apt-get install zlib1g-dev:i386
```

ah yea that solved it thnx  :)

---

