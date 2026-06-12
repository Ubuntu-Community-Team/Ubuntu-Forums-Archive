---
title: "gcc 4.6 to 4.7 Ubuntu 12.04"
date: 2012-08-30
forum: Packaging and Compiling Programs
---

### Post by larzconwell on 2012-08-30
So I'm working on a project and I wanted to use some C11 features for C. To use those features GCC 4.7 is required, so I went to synaptic and looked up 4.7, and I found the packages gcc-4.7-base so I installed it[1].

So now that gcc-4.7-base is installed I expected to be able to use 4.7, but no, when I do gcc --version it still shows 4.6.3 even more, when I try to directly call 4.7(via /usr/bin/gcc-4.7) it doesn't exist, though a gcc-4.6 executable does exist.

How do I "activate" GCC 4.7? I read you can do some crazy stuff with update-alternatives to update the cc/gcc/g++ links to 4.7, but it doesn't work for me as the gcc-4.7 executable doesn't actually exist on my machine.

Notes: 1. I also saw gcc-4.6-base, so I figured I'd uninstall it, but synaptic attempted to remove every package I had installed and install a Java runtime, so for obvious reason I decided not to remove it.

---

### Post by Bachstelze on 2012-08-30
gcc 4.7 is not available on the Precise repositories. Upgrade to Quantal, or use anothe rdistribution. You could try to install the gcc 4.7 packages from the Quantal repositories, but that could lead to problems.

---

### Post by larzconwell on 2012-08-30
Okay so what is the gcc-4.7-base package that's found in the repos?

---

### Post by Bachstelze on 2012-08-30
It seems it's only there because it's needed by the Go frontend to GCC 4.7, which is in Precise. The C frontend is not.

---

### Post by MadCow108 on 2012-08-30
if you want to install 4.7 you should use a backport from a ppa, e.g. from [https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)

installing the one from quantal might cause more issues.

---

### Post by SevenMachines on 2012-09-02
> **MadCow108 said:**
> if you want to install 4.7 you should use a backport from a ppa, e.g. from [https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)


+1 for this, use a virtual machine for this if possible though, if you've got a reasonably new machine it can be perfect for testing out toolchains

---

