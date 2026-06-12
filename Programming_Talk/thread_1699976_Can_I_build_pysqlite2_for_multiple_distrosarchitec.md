---
title: "Can I build pysqlite2 for multiple distros/architectures"
date: 2011-03-04
forum: Programming Talk
---

### Post by tgm4883 on 2011-03-04
I attempted searching for this info, but couldn't find it. It either doesn't exist or my lack of experience with compiling contributes to my issue. I've posted this here as I do all of my dev work on Ubuntu systems and don't run other distros except for testing the software on.

I've written a python program that uses sqlite to write to a db file. I've tested this and it works great on my Ubuntu 10.10 system, as well as any other distros that have python 2.5 or later. I need it to work on systems with python 2.3 or later.

I thought I had resolved this by downloading pysqlite-2.6.3 source and compiling it on a CentOS 32-bit and 64-bit system with Python 2.3 and Python 2.4. This worked on all of the systems I tested (CentOS and RHEL 4+), but had the negative side effect of making the program much larger than it needed to be.

The issue cropped up again when a colleague tested on Suse 10 machine. I was presenting with Floating Point errors when trying to run my program. Compiling pysqlite-2.6.3 from source on the Suse machine resolved this issue, however I think I'll now need to compile it 4 times for the Suse systems now. I also may run into the same issue on other distributions.

My question is this. Is there some way I can compile pysqlite2 once and run it on all platforms? (or at least not have to build it for each individual distro/arch/python version).

---

### Post by tgm4883 on 2011-03-07
Bump

---

### Post by tgm4883 on 2011-03-07
The Suse issue I was running into was apparently due to the pysqlite2 module being compiled for Python 2.4.4, while the Suse box I had was Python 2.4.3. I was able to remedy this by using the pysqlite2 module that was compiled for Python 2.3 for the Suse machine.

As an added benefit, I found I can get rid of the compiled for Python 2.4 versions, although I still have to compile for each architecture.

---

