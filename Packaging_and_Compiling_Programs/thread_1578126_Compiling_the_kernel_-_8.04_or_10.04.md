---
title: "Compiling the kernel - 8.04 or 10.04?"
date: 2010-09-19
forum: Packaging and Compiling Programs
---

### Post by dhalperi on 2010-09-19
Hi,

I do driver development work and as such want to run a kernel from an upstream GIT repository rather than from Ubuntu.  When I started this work 2 years ago, we used Ubuntu 8.04 and kernel-package for our machines.

I'd like to upgrade to 10.04, because a lot of things are pretty outdated in 8.04 and it will go out of service soon, but as far as I can tell there's just too many things that have broken with non-Ubuntu custom kernels since then.  Can anyone help me resolve these issues?

I installed 10.04 server x86. and I tried to follow the instructions [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) to compile the kernel.

This failed because dpkg-gencontrol complains that the version I want to compile isn't in the control info.  I tried everything I found while googling for that error ([http://www.mail-archive.com/debian-user@lists.debian.org/msg199248.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg199248.html)) and nothing useful helped.  I tried both of the kernel settings they suggested.

Then I tried to reinstall 8.04, but the new server livecd (8.04.4) doesn't even boot unless I edit grub and add all_generic_ide.  SCARY.

Has ubuntu totally jumped the shark?  Why does nothing work?  What can I do to resolve these issues?  Does anyone actually have experience running a non-Canonical kernel with 10.04 and having a useable dev process (i.e., don't have to manually edit text files every time you run a git-pull)?

Thanks,
Dan

---

### Post by Yellow Pasque on 2010-09-29
Can you paste the exact output?

---

