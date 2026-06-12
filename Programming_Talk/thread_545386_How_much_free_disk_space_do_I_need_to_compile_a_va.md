---
title: "How much free disk space do I need to compile a vanilla kernel"
date: 2007-09-07
forum: Programming Talk
---

### Post by kevdog on 2007-09-07
Ive downloaded and compiled the latest vanilla kernel 2.6.22.6.  The entire source directory was 2.9 Gb in size after compilation.  How much additional space is needed for the installation of the kernel -- Ive tried to install however I get an error somewhere in the installation step that Im out of disk space when I have roughly 3gb remaining on the partition.

---

### Post by Bachstelze on 2007-09-07
It all depends on which options you choose. As I told you, on my machine, kernel compilation takes roughly 500 MB of diskpace. For the most part, it will be easy for you to tell whether you need a module or not (either you own the relevant hardware, or you do not). Try disabling as many unnecessary modules as you can and compiling again.

---

