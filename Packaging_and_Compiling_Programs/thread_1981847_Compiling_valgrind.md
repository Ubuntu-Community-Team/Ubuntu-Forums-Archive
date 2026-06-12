---
title: "Compiling valgrind"
date: 2012-05-17
forum: Packaging and Compiling Programs
---

### Post by microbot on 2012-05-17
I hope it is ok to post questions about valgrind here.

I am following learncthehardway.com's  C tutorial. The line numbers in the valgrind report are not printing, even with -g in makefile. That makes it harder to debug  by far.

Makefile: 
((-
CFLAGS=-Wall -g

clean:
    rm -f ex4
-))

I have been searching for two days. I am not having much luck.
Thanks in advance.

Ubuntu 12.04., 3.2.0-24-generic-pae,
 Valgrind-3.7.0, make 3.81

---

### Post by oldos2er on 2012-05-17
Post moved to its own thread.

---

### Post by Bachstelze on 2012-05-17
> **oldos2er said:**
> Post moved to its own thread.

The new title is a little misleading: OP doesn't want to compile Valgrind itself, but compile some other code and examine it in Valgrind.

@microbot: We need more information. In particular, describe the code in more detail (what is it? where does it come from?), and post the entire Makefile.

---

### Post by microbot on 2012-05-17
me@Earth:~/c$ valgrind ./ex5
==27832== Memcheck, a memory error detector
==27832== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
==27832== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
==27832== Command: ./ex5

-
-
-
-
-
==27832== 
==27832== 
==27832== HEAP SUMMARY:
==27832==     in use at exit: 0 bytes in 0 blocks
==27832==   total heap usage: 0 allocs, 0 frees, 0 bytes allocated
==27832== 
==27832== All heap blocks were freed -- no leaks are possible
==27832== 
==27832== For counts of detected and suppressed errors, rerun with: -v
==27832== Use --track-origins=yes to see where uninitialised values come from
==27832== ERROR SUMMARY: 19 errors from 15 contexts (suppressed: 0 from 0)

This is an example. I have no line numbers.

---

### Post by Bachstelze on 2012-05-17
Of course you get no line numbers, there are no problems. ;) Valgrind reports problems in your code, including the line where the problem occurs. If there are no problems, there is nothing to report.

---

### Post by microbot on 2012-05-17
Funny. It doesn't even display them at all ?

((-
==27832== Conditional jump or move depends on uninitialised value(s)
==27832==    at 0x804E405: malloc (in /home/me/c/ex5)
==27832==    by 0x62696C2E: ???
==27832== 
==27832== Conditional jump or move depends on uninitialised value(s)
==27832==    at 0x804E42A: malloc (in /home/me/c/ex5)
==27832==    by 0x62696C2E: ???
==27832== 
-))

Is the above not an error?

When the program was right I got this. its a lot shorter. I didn't post the whole error last time as it was long.

((-
me@Earth:~/c$ valgrind ./ex5
==27777== Memcheck, a memory error detector
==27777== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
==27777== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
==27777== Command: ./ex5
==27777== 
you are 100 miles away.
==27777== 
==27777== HEAP SUMMARY:
==27777==     in use at exit: 0 bytes in 0 blocks
==27777==   total heap usage: 0 allocs, 0 frees, 0 bytes allocated
==27777== 
==27777== All heap blocks were freed -- no leaks are possible
==27777== 
==27777== For counts of detected and suppressed errors, rerun with: -v
==27777== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

-))

---

### Post by Bachstelze on 2012-05-17
Well, stop giving partial information. First I asked you something. You answered with something else, and again that was something that did not demonstrate the problem. Maybe if you start giving complete information, someone else will help you. I won't.

---

### Post by microbot on 2012-05-18
many pardons, trying not to be rude on forums. new to this.

---

