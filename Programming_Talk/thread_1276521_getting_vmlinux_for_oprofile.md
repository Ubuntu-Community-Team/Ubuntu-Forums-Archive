---
title: "getting vmlinux for oprofile"
date: 2009-09-27
forum: Programming Talk
---

### Post by napsy on 2009-09-27
Hello.

I'm trying to profile my program but need an uncompressed kernel image (vmlinux not the compressed vmlinuz image that is provided by default). I've searched for a development kernel package which doesn't have symbols stripped out and has an uncompressed image but failed.

Is there some hidden trick to get the debug kernel or do I really have to compile the kernel from source to get what I want.

$ uname -a
Linux sfinga 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux

Greets.

---

### Post by articfox on 2010-01-25
I have the same question.  Anyone?

---

### Post by sendmoreinfo on 2010-12-22
Enable ddebs.ubuntu.com repository and install linux-image...dbgsym package.

[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

---

