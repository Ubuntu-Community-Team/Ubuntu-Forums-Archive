---
title: "Compiled programs on older machines"
date: 2007-04-05
forum: Programming Talk
---

### Post by sYnie on 2007-04-05
Hello,

I'm a server administrator. I wrote some little helper tools in C++ for my Servers. Every single one is compiled on my local Notebook, 2.6.17-11-386, Kubuntu Edgy Eft. They are all compiled statically. Till the last `apt-get upgrade` on my Notebook, they worked without any problems on my older server machines. But when I recompile them now (after the Update), they just work on machines with a 2.6.* kernel running. Unfortunately I cant remember the packages, got updated.
So when I look at the binaries with `file`, I get those outputs:
For the old ones:
ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, statically linked, for GNU/Linux 2.2.0, not stripped
For the new ones:
ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, statically linked, for GNU/Linux 2.6.0, not stripped

The error I'll get, when I try to run a recompiled binary on a SuSe 9.1 Server with a 2.4.29 Kernel:
FATAL: kernel too old
Segmentation fault

I think the apt-get upgrade updated my libc. But I have no ideas what to do, to get those programs run on the servers.
I can't update the servers and I don't want to recompile the programs on the servers. So is there a way to use an old libc to compile the programs? Or is there any other way, to get the programs work on such old machines?

Regards,
Mario

---

