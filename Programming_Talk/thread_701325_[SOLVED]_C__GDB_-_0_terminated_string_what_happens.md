---
title: "[SOLVED] C / GDB - \0 terminated string: what happens to tail of string?"
date: 2008-02-19
forum: Programming Talk
---

### Post by tehet on 2008-02-19
Hi,
I'm going through [this pointer tutorial](http://home.netcom.com/~tjensen/ptr/pointers.htm) which suggests to run [program 3.1](http://home.netcom.com/~tjensen/ptr/ch3x.htm) through a debugger. My slightly modified version looks like this:
```
/* Program 3.1 from PTRTUT10.HTM   6/13/97 */

#include <stdio.h>

char strA[80] = "A string to be used for demonstration purposes";
char strB[80] ="12345678901234567890123456789012345678901234567890";

int main(void)
{

    char *pA;     /* a pointer to type character */
    char *pB;     /* another pointer to type character */
    puts(strA);   /* show string A */
    pA = strA;    /* point pA at string A */
    puts(pA);     /* show what pA is pointing to */
    pB = strB;    /* point pB at string B */
    putchar('\n');       /* move down one line on the screen */
    while(*pA != '\0')   /* line A (see text) */
    {
        *pB++ = *pA++;   /* line B (see text) */
    }
    *pB = '\0';          /* line C (see text) */
    puts(strB);          /* show strB on screen */
    pB = pB + 10;
    printf("bla\n");
    return 0;
}
```
When I run it in GDB this happens:
```
~/test$ gdb testprog2
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) b main
Breakpoint 1 at 0x80483b5: file testprog2.c, line 13.
(gdb) r
Starting program: /home/tehet/test/testprog2

Breakpoint 1, main () at testprog2.c:13
13          puts(strA);   /* show string A */
(gdb) n
A string to be used for demonstration purposes
14          pA = strA;    /* point pA at string A */
(gdb)
15          puts(pA);     /* show what pA is pointing to */
(gdb)
A string to be used for demonstration purposes
16          pB = strB;    /* point pB at string B */
(gdb)
17          putchar('\n');       /* move down one line on the screen */
(gdb)

18          while(*pA != '\0')   /* line A (see text) */
(gdb)
20              *pB++ = *pA++;   /* line B (see text) */

...
<snip>
...

18          while(*pA != '\0')   /* line A (see text) */
(gdb)
20              *pB++ = *pA++;   /* line B (see text) */
(gdb) p strB
$6 = "A string to be used for demonstration purpose67890", '\0' <repeats 29 times>
(gdb) n
18          while(*pA != '\0')   /* line A (see text) */
(gdb)
22          *pB = '\0';          /* line C (see text) */
(gdb) p strB
$7 = "A string to be used for demonstration purposes7890", '\0' <repeats 29 times>
(gdb) n
23          puts(strB);          /* show strB on screen */
(gdb)
A string to be used for demonstration purposes
24          pB = pB + 10;
(gdb) p strB
$8 = "A string to be used for demonstration purposes\000890", '\0' <repeats 29 times>
(gdb) p pB
$9 = 0x80496ce ""
(gdb) n
25          printf("bla\n");
(gdb)
bla
26          return 0;
(gdb)
27      }
(gdb)
0xb7e59050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
(gdb)
Single stepping until exit from function __libc_start_main,
which has no line number information.

Program exited normally.
```
When strB gets \0 terminated it changes from "... purposes**7890**", '\0' <repeats 29 times>" to "... purposes**\000890**", '\0' <repeats 29 times>". Is that to be expected, i.e. that 7 gets replaced by \000? Or am I not using GDB properly?

At the end I expect strB to be
A string to be used for demonstration purposes\00000000000000000000000000000000000000000...
Why, after **pB = pB + 10;**, does **p pB** return rvalue "" and not "0"?

Is the backslash of \0 just for programmers or is it actually there in memory? So does strB actually look like this?
A string to be used for demonstration purposes\000890\00000000000000000000000000000000000 ...

Thanks.

---

### Post by jrib on 2008-02-19
As I understand it, strB is "A string to be used for demonstration purposes\0890\0\0\0\0\0\0\0\0\0\0\0... 33 times ...\0\0\0\0\0" since your loop stops right before it copies the first '\0' in strA and then the place where *pB is set to '\0' on the line after the loop

gdb just prints NULL ('\0') as \000.  I think there must be a typo in the tutorial and what was meant was that you do pB = pB +1.  Then pB points to the 8 in strB and when you print pB you should get "890" and then it hits the first of the 33 \0

---

### Post by tehet on 2008-02-19
> **_jason said:**
> As I understand it, strB is "A string to be used for demonstration purposes\0890\0\0\0\0\0\0\0\0\0\0\0... 33 times ...\0\0\0\0\0" since your loop stops right before it copies the first '\0' in strA and then the place where *pB is set to '\0' on the line after the loop

gdb just prints NULL ('\0') as \000.
Thanks, that clears it up for me!
> I think there must be a typo in the tutorial and what was meant was that you do pB = pB +1.  Then pB points to the 8 in strB and when you print pB you should get "890" and then it hits the first of the 33 \0
I added the pB + 10 thing myself because I wanted to see what the rvalue is of a pointer that points to the tail of a \0 terminated string. Apparently nothing (or NULL).

---

