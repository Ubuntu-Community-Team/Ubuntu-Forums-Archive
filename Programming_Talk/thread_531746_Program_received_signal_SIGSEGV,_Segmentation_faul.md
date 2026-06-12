---
title: "Program received signal SIGSEGV, Segmentation fault"
date: 2007-08-21
forum: Programming Talk
---

### Post by nonoykevin on 2007-08-21
hey there!

I'm trying to debug my program. i use the gdb as my debugging application. first i link all my source codes using make (makefile), then i use gdb test to debug the program. after which, i use the run command [ (gdb) run] to check for any possible error on my program. below are the  result messages:

Starting program:
[Thread debugging using libthread_db enabled]
[New Thread - 1211099440 (LWP 5322)]

Program received signal SIGSEV, segmentation fault
[switching to thread - 1211099440 (LWP 5322)
0xb7f73442 in pthread_cond_destroy@@GLIBC_2.3.2 

Can somebody explain to me what does this mean?
I'm just a newbie user of gdb.

Thanks a lot!

---

### Post by foxylad on 2007-08-21
A segfault means your program is writing to memory that it shouldn't. Rather than "run", use "next" and "skip" to step through your program - then you'll find where the segfault is actually occurring.

Also make sure you compile with -g so it puts debug info into the executable. Then your gdb session should look like this:

gdb test
b main
r
n
n
n
n
...

"b main" sets a break point at main().
"r" runs till that breakpoint.
"n" steps to the next instruction.

For much more really useful stuff, see the gdb docs. Good luck!

---

### Post by hello007 on 2010-10-19
Hi, 
 
Could you tell me why I am getting segmentation fault after debuging a shared object file (test.so).  For better understanding, commands are following:
 
 
 
$ gdb test.so
 
(gdb) b 89
Breakpoint 1 at 0x1a1e6: file src/rTest.cpp, line 89.
 
(gdb) run
Starting program: test.so
Breakpoint 1 at 0x7b01e6: file src/rTest.cpp, line 89.
Program received signal SIGSEGV, Segmentation fault.
0x00000001 in ?? ()

---

### Post by dwhitney67 on 2010-10-19
Why did you resurrect an old thread?

As for your question, nobody will be able to offer you precise help because you did not post your code.  All I can say is to look at this file, src/rTest.cpp, at line 89; maybe your answer is there or somewhere after, or perhaps somewhere before.

---

### Post by Barrucadu on 2010-10-19
Additionally, run your program with Valgrind and fix everything it reports.

---

