---
title: "Dependency problem with libc6-dev"
date: 2006-06-19
forum: Repositories &amp; Backports
---

### Post by cardogar on 2006-06-19
Hi,

I've just installed the intel fortran compiler version 9.0.031 in my ubuntu breezy 2.6.12-10-686, but I find the following error when I try to compile:

IPO link: can not find "/usr/lib/crt1.o"
ifort: error: problem during multi-file optimization compilation (code 1)

I've checked the repository packages and ctr1.o library is included in libc6-dev package, which I don't have installed.

But if I try to install the libc6-dev with 'aptitude' I get the next error:

carlos@meteoro:~/Desktop$ sudo aptitude install libc6-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu12) but 2.3.5-1ubuntu12.5.10.1 is installed.

If I try with the deb package I reach the same error:

dpkg: dependency problems prevent configuration of libc6-dev:
libc6-dev depends on libc6 (= 2.3.5-1ubuntu12); however:
Version of libc6 on system is 2.3.5-1ubuntu12.5.10.1.

I've looked for the package details of libc6 with the synaptic:

2.3.5-1ubuntu12.5.10.1 (now)
2.3.5-1ubuntu12 (breezy)

I need the second version since it is needed for the libc6-dev, but I have installed the first one. I don't know why I have installed this version... but is possible to downgrade until the 2.3.5-1ubuntu12?

Or, is there any alternative solution to install the libc6-dev?

Sorry for my bad english #-o 

Thanks for your attention and help.

Cheers.

---

