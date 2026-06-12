---
title: "System Calls? Ubuntu."
date: 2014-06-20
forum: Programming Talk
---

### Post by kozuefan10 on 2014-06-20
Hi all,

Just a general question, I'm currently taking a computer science course in Operating Systems and I was wondering are the system calls for all linux distros the same?

kozuefan10.

---

### Post by oldos2er on 2014-06-20
Moved to Programming Talk.

---

### Post by trent.josephsen on 2014-06-20
A system call is by definition a kernel feature, so if there are differences between those available on different distros, it's because the distros use different kernels. This could be due to distro-specific patches, but I don't think I've ever heard of distros patching the kernel to add or remove a syscall. However, since different distros use different *versions* of the Linux kernel, there are definitely syscalls available on some and not others.

[Here's](http://manpages.ubuntu.com/manpages/trusty/man2/syscalls.2.html) a list of Linux system calls, some of which have the kernel version they first appeared in.

---

### Post by ofnuts on 2014-06-21
Differences can come from build options or kernel versions (stuff in V3 kernels that you won't find in V2 kernels). But distros for the general public are likely to have very similar kernel build options, and I would expect more differences between two successive releases of the same distro than between two different distros published at about the same time. But I doubt any of these differences would be important for your class (and if they ever become so, you'll then be able to recompile your own kernel...).

---

