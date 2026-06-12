---
title: "Segfault, freeglut_main.c not found, wtf?"
date: 2009-01-17
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-17
I got a program, which uses GLUT. But when I run it, it gives me a segmentation fault.

And gdb says:
> 
arho@arho-laptop:~/C/miniTDS$ gdb mapEditor
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) break 85
Breakpoint 1 at 0x40193d: file editor.c, line 85.
(gdb) run
Starting program: /home/arho/C/miniTDS/mapEditor 
[Thread debugging using libthread_db enabled]
[New Thread 0x7ffa5553f730 (LWP 7037)]
[Switching to Thread 0x7ffa5553f730 (LWP 7037)]

Breakpoint 1, main (argc=1, argv=0x7fff5d731bd8) at editor.c:87
87	    glutMainLoop();
(gdb) step
glutMainLoop () at freeglut_main.c:1008
1008	freeglut_main.c: No such file or directory.
	in freeglut_main.c
(gdb) 

After that, it will keep saying "freeglut_main.c: No such file or directory.", and won't proceed.

I installed ALL glut packages with apt, devs, dbgs and docs as well, and it still doesn't work.

So glutMainLoop() is causing this problem. What's wrong? How to fix it?

---

### Post by dexter on 2009-01-17
You're using the library but you probably don't have the source installed. That's why gdb gives this error. Try installing the source from the repository. 
If it's not available there, download the libraries code, compile it yourself and use this to link with your program. gdb will be able to find the source code.

edit: you can use apt-get source to install source code from the repository.

---

### Post by eye208 on 2009-01-17
> glutMainLoop () at freeglut_main.c:1008
1008 freeglut_main.c: No such file or directory.
in freeglut_main.c
This probably means that the error is occurring at line 1008 in freeglut_main.c, not that freeglut_main.c itself is missing. But I'm not familiar with gdb, so I'm just guessing.

---

### Post by Zugzwang on 2009-01-17
By the way: Segmentation faults can be best debugged with "valgrind". Search in the forum to get some examples on its usage.

---

### Post by crazyfuturamanoob on 2009-01-17
Oh crap I just realized I'm trying to debug an old executable :x

For first, output executable name was "mapEditor", then I changed it to "editor", while I was debugging old, compiled mapEditor!

Daaaaamn! The new one works perfectly, and I made it triple-safe while trying to debug the old binary. (fixed string stuff, added a lot NULL checkings, warnings, error checking etc)


And I accidentally posted this into wrong thread before posting it here.

This isn't my day. Everything goes wrong.

](*,)

---

