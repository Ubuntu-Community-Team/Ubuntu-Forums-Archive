---
title: "Compiling 2.6.30-rc2 for lpia, &quot;kimagedest undefined&quot;"
date: 2009-04-17
forum: Packaging and Compiling Programs
---

### Post by Zorael on 2009-04-17
I have an Advent 4211 (rebranded MSI Wind) netbook, and I thought I'd try an MID/lpia installation. Everything works, but when I want to compile a new kernel to get KMS, I hit a wall. I normally use kernelcheck, but it freaked out on me and failed to compile, so I'm taking commands from the master kernel thread. Only even when trying to compile normally, it freaks out similarly.

I'm compiling on the same system I'd like to use the kernel on, so no architectural differences.
```
# uname -a
Linux lethe 2.6.28-11-lpia #41-Ubuntu SMP Wed Apr 8 04:37:31 UTC 2009 i686 GNU/Linux
```

```
# CONCURRENCY_LEVEL=3 make-kpkg --initrd kernel_image kernel_headers modules_image
exec debian/rules  DEBIAN_REVISION=2.6.30-rc2-kms-10.00.Custom  INITRD=YES  kernel_image kernel_headers modules_image
[: 1: -lt: unexpected operator
[: 1: -gt: unexpected operator
[: 1: -lt: unexpected operator
[: 1: -lt: unexpected operator
[: 1: -eq: unexpected operator
[: 1: -eq: unexpected operator
[: 1: -eq: unexpected operator
debian/ruleset/misc/checks.mk:36: *** Error. I do not know where the kernel image goes to [kimagedest undefined] The usual case for this is that I could not determine which arch or subarch this machine belongs to. Please specify a subarch, and try again..  Stop.
```
I tried playing with *--arch lpia* and/or *--subarch lpia*, but that didn't seem to have any effect. The architecture should still be i686, right?

Anything obvious I've done wrong or have yet to do? Do I need to add extra stuff to the kernel to get it to support being compiled as aimed towards lpia?

The 2.6.28-11 source from repositories seems to have some lpia stuff that the kernel.org 2.6.29 patched to 2.6.30rc2 doesn't.
```
linux-2.6.28$ find | grep lpia
./debian/config/lpia
./debian/config/lpia/config.lpia
./debian/config/lpia/config
./debian/abi/2.6.28-11.41/lpia
./debian/abi/2.6.28-11.41/lpia/lpia
./debian/abi/2.6.28-11.41/lpia/lpia.modules
./debian/control.d/vars.lpia
./debian/rules.d/lpia.mk
./sound/pci/hda/lpia_ubuntu_patch_sigmatel.c

linux-2.6.29# find | grep lpia
*<nothing>*
```
Further noteworthy is that I get the same error when trying to compile that repository 2.6.28-11 source.
```
linux-2.6.28# CONCURRENCY_LEVEL=3 make-kpkg --initrd kernel_image kernel_headers modules_image
exec debian/rules  DEBIAN_REVISION=2.6.28-11.42  INITRD=YES  kernel_image kernel_headers modules_image
[: 1: -lt: unexpected operator
[: 1: -gt: unexpected operator
[: 1: -lt: unexpected operator
[: 1: -lt: unexpected operator
[: 1: -eq: unexpected operator
[: 1: -eq: unexpected operator
[: 1: -eq: unexpected operator
debian/ruleset/misc/checks.mk:36: *** Error. I do not know where the kernel image goes to [kimagedest undefined] The usual case for this is that I could not determine which arch or subarch this machine belongs to. Please specify a subarch, and try again..  Stop.
```

; /

---

### Post by Lord Alexander on 2009-04-18
I'll be curious to hear the solution to this.  I have the same issue, compiling a patched 2.6.28-11 (patched by me) for lpia.  I can't believe there's no faq for this.  Oh well.

---

### Post by lokad on 2009-07-07
Exactly the same problem here with 2.6.31-2-lpia (Ubuntu 9.10 alpha 2)
I need to activate the rt2860 driver in staging for wireless on my Asus EEE 1000H

---

### Post by Andareed on 2009-08-13
You need to set KPKG_ARCH=i686 (or pass '--arch i686') and pass '--cross-compile -' to make-kpkg.

---

