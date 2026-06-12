---
title: "Trouble bisecting a kernel"
date: 2011-02-19
forum: Packaging and Compiling Programs
---

### Post by xghstst0riesx on 2011-02-19
I'm trying to bisect a kernel to fix a bug I filed - [https://bugs.launchpad.net/bugs/721954]("https://bugs.launchpad.net/bugs/721954"). I'm following the directions on [https://wiki.ubuntu.com/Kernel/KernelBisection]("https://wiki.ubuntu.com/Kernel/KernelBisection") but am running into a roadblock. After my first bisection, the resulting source tree does not have any of the debian directories and thus I cannot update the version number as detailed in the "Give this test a version number" section of the tutorial.

I checked out the code with these commands:
```

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git
cd ubuntu-maverick
git checkout -b mybisect origin/master

```

Then started the bisection:
```
patrick@ceo:~/code/kernel-maverick/ubuntu-maverick$ git bisect start Ubuntu-2.6.35-22.35 Ubuntu-2.6.34-1.1
Bisecting: a merge base must be tested
[220bf991b0366cc50a94feede3d7341fa5710ee4] Linux 2.6.34-rc2
patrick@ceo:~/code/kernel-maverick/ubuntu-maverick$ ll
total 452
drwxr-xr-x 25 patrick patrick   4096 2011-02-19 17:25 arch/
drwxr-xr-x  2 patrick patrick   4096 2011-02-19 17:25 block/
-rw-r--r--  1 patrick patrick  18693 2011-02-19 16:55 COPYING
-rw-r--r--  1 patrick patrick  94031 2011-02-19 16:55 CREDITS
drwxr-xr-x  3 patrick patrick   4096 2011-02-19 17:25 crypto/
drwxr-xr-x 85 patrick patrick  12288 2011-02-19 17:25 Documentation/
drwxr-xr-x 89 patrick patrick   4096 2011-02-19 17:25 drivers/
drwxr-xr-x 36 patrick patrick   4096 2011-02-19 17:25 firmware/
drwxr-xr-x 72 patrick patrick   4096 2011-02-19 17:25 fs/
drwxr-xr-x 20 patrick patrick   4096 2011-02-19 17:25 include/
drwxr-xr-x  2 patrick patrick   4096 2011-02-19 17:25 init/
drwxr-xr-x  2 patrick patrick   4096 2011-02-19 17:25 ipc/
-rw-r--r--  1 patrick patrick   2440 2011-02-19 16:55 Kbuild
drwxr-xr-x  7 patrick patrick   4096 2011-02-19 17:25 kernel/
drwxr-xr-x  6 patrick patrick   4096 2011-02-19 17:25 lib/
-rw-r--r--  1 patrick patrick 170026 2011-02-19 17:25 MAINTAINERS
-rw-r--r--  1 patrick patrick  53204 2011-02-19 17:25 Makefile
drwxr-xr-x  2 patrick patrick   4096 2011-02-19 17:25 mm/
drwxr-xr-x 48 patrick patrick   4096 2011-02-19 17:25 net/
-rw-r--r--  1 patrick patrick  17459 2011-02-19 16:55 README
-rw-r--r--  1 patrick patrick   3371 2011-02-19 16:55 REPORTING-BUGS
drwxr-xr-x  7 patrick patrick   4096 2011-02-19 16:55 samples/
drwxr-xr-x 12 patrick patrick   4096 2011-02-19 17:25 scripts/
drwxr-xr-x  7 patrick patrick   4096 2011-02-19 17:25 security/
drwxr-xr-x 21 patrick patrick   4096 2011-02-19 17:25 sound/
drwxr-xr-x  3 patrick patrick   4096 2011-02-19 17:25 tools/
drwxr-xr-x  2 patrick patrick   4096 2011-02-19 17:25 usr/
drwxr-xr-x  3 patrick patrick   4096 2011-02-19 16:55 virt/

```

Is there something I'm doing wrong? Does this source tree not have the debian specific directories in it at all times?

---

