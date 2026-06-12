---
title: "Compiling on one machine and executing on another (C/C++)"
date: 2010-07-03
forum: Packaging and Compiling Programs
---

### Post by eladna on 2010-07-03
Basic question about Linux:
Can I compile a source C/C++ code to an executable file on my Ubuntu x64 machine and then run it on another machine?
(considering that they both running on x64 bit and running Linux, but not necessarily the same distribution of Linux)

Thanks!

---

### Post by Bachstelze on 2010-07-03
Yes, although of course if your code uses some library, you must make sure the other machine has those libraries as well (also take care of CPU-specific compiler opimisations if the machines have different CPUs).

---

