---
title: "My version of mono is 1.1.13..6 how to upgrade?"
date: 2007-03-15
forum: Programming Talk
---

### Post by hecato on 2007-03-15
Hi there people, the problem is that I dont know if this versions are "normal" in the repos or should I add another repo to my lists???

> tyoc@redcontel:~$ mono --version
Mono JIT compiler version 1.1.13.6, (C) 2002-2005 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
        TLS:           __thread
        GC:            Included Boehm (with typed GC)
        SIGSEGV      : normal
tyoc@redcontel:~$ cat /proc/version
Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
tyoc@redcontel:~$ uname --all
Linux redred 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux


I whant to use MoMA by instance, but it say it need at least 1.2.3 wich isnt show in the versions in the repos via synaptic.

---

### Post by blanky on 2007-03-15
I only have 1.1.17.1, but I figure you can get the latest one using Backports. Search the wiki for backports and it should show you how to enable backports, which will let you get the latest versions of many programs.

---

