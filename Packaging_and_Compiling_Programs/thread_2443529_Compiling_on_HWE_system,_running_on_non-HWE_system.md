---
title: "Compiling on HWE system, running on non-HWE system"
date: 2020-05-16
forum: Packaging and Compiling Programs
---

### Post by &amp;KyT$0P# on 2020-05-16
Suppose I were to compile some software on a Xubuntu 18.04 machine running the HWE kernel and the stock/non-HWE X server.  Will the resulting binaries have issues running on a totally non-HWE Xubuntu 18.04?

Said machine had HWE kernel installed "after the fact" - i.e., it had the stock 4.15 kernel when the system was first installed, and the HWE kernel was manually added following [this method]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").  And the stock 4.15 kernel was not uninstalled after upgrading to the HWE kernel.

---

### Post by &amp;KyT$0P# on 2020-05-19
Maybe I could have asked the question slightly differently: Is it safe to assume that if I just try this and don't see any **immediate** problems, that it's fine?

Searching further turned up [this](https://stackoverflow.com/questions/27171485/various-glibc-and-linux-kernel-versions-compatibility), which links [this]("https://sourceware.org/glibc/wiki/FAQ#What_version_of_the_Linux_kernel_headers_should_be_used.3F"), but I don't understand this stuff well enough to know what to make of that or how that info might relate to my question?

---

### Post by Yellow Pasque on 2020-05-26
It depends on what you're building. If it's a kernel module or something else that builds against the kernel headers, then you will probably have issues. If not, it shouldn't make a difference.

---

### Post by &amp;KyT$0P# on 2020-05-26
Thanks Yellow Pasque!  The software I would do this with doesn't contain kernel modules as far as I know, so it sounds like this should be fine.

And for other cases: if it's the version of the kernel *headers* that matters, not the running kernel version, surely it would be possible to specifically specify to compile against the installed 4.15 kernel headers and thus should still be fine, just might take an extra step.

---

