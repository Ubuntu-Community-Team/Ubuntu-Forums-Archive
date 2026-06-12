---
title: "Running gdb core dump"
date: 2011-12-13
forum: Programming Talk
---

### Post by bikewrecker on 2011-12-13
Hi guys, I'm having troubble figuring out how to analyze the core dump of my code using gdb. according to the website: [http://www.cprogramming.com/debugging/segfaults.html](http://www.cprogramming.com/debugging/segfaults.html), I meerly need to type in   
$gdb radxfer core

and it will tell me everything i need to know; however, when I type this in I get:
```

daniel@daniel-EP45-UD3L:~/Desktop/CProgramming/Project$ gdb radxfer core
GNU gdb (Ubuntu/Linaro 7.3-0ubuntu2) 7.3-2011.08
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /home/daniel/Desktop/CProgramming/Project/radxfer...(no debugging symbols found)...done.
/home/daniel/Desktop/CProgramming/Project/core: No such file or directory.
(gdb) ^Z
[4]+  Stopped                 gdb radxfer core

```

I don't know what its telling me. Any ideas would be very much appreciated.

---

### Post by Bachstelze on 2011-12-14
For starters, no, gdb will not "tell you everything you need to know". It is just a tool, not a magic wand. You will have some investigating to do yourself (how much depends on the problem).

This is especially true if, as is the case here, you compiled without the -g flag (which adds debugging symbols, without which gdb is pretty much useless).

Finally, you obviously need to replace "core" with the name of the core dump file. I think by default core dumps are disabled, run

```
ulimit -c unlimited
```

to enable them. Also, here's [a good gdb tutorial](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/CLanguage/Debug.html). You sound like you will need it.

---

### Post by MadCow108 on 2011-12-14
you can just start the program in gdb to begin with if you can reproduce the crash:
```
gdb --args ./myprogram --my-commandlineoptions
> run
#wait for segfault
> backtrace 
```

---

### Post by karlson on 2011-12-14
> **MadCow108 said:**
> you can just start the program in gdb to begin with if you can reproduce the crash:
```
gdb --args ./myprogram --my-commandlineoptions
> run
#wait for segfault
> backtrace 
```

If you know that program will reach the segfault or if you know exactly how to reproduce the conditions leading to a segfault then this will work.

---

