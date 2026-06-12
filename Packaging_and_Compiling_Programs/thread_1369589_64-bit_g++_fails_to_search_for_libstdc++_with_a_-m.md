---
title: "64-bit g++ fails to search for libstdc++ with a -m32 option"
date: 2010-01-01
forum: Packaging and Compiling Programs
---

### Post by hpsmouse on 2010-01-01
I was using 64-bit Jaunty and everything went well.
But after I upgraded to Karmic, g++ started to fail when ordered to compile a 32-bit program, using option -m32. The message is like this:
> /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

I am sure there is a 32-bit version libstdc++.so.6 in /usr/lib32, but even if I add the path with -L option, exactly the same message is printed.
Compiling a C program with gcc have no problem.

---

### Post by SevenMachines on 2010-01-02
try,
$sudo apt-get install g++-multilib
and give it another bash

---

### Post by hpsmouse on 2010-01-03
> **SevenMachines said:**
> try,
$sudo apt-get install g++-multilib
and give it another bash
Thanks a lot!
It works!

---

