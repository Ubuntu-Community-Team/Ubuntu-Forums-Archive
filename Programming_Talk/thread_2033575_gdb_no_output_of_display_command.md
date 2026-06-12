---
title: "gdb: no output of display command"
date: 2012-07-26
forum: Programming Talk
---

### Post by icegood on 2012-07-26
Already posted to [nabble](http://old.nabble.com/display-command-td34216676.html).
Does anyone have same? 

My system is kubuntu 12.04

---

### Post by dwhitney67 on 2012-07-26
WTF?

You expect readers to go to another site to see your query?

If you have an issue with using gdb, say so here!

---

### Post by icegood on 2012-07-26
> **dwhitney67 said:**
> WTF?

You expect readers to go to another site to see your query?

If you have an issue with using gdb, say so here!
No problem... I just think like programmer - better to do pointer than copy-paste. But if you insist...

Have GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04. 
Display command doesn't work at all. Nothing displayed thought no errors returned. 
Print command works, so at least stdout (or whatever) is OK. 
Am i specific or is it well-known issue?

---

### Post by the_unforgiven on 2012-07-27
> **icegood said:**
> No problem... I just think like programmer - better to do pointer than copy-paste. But if you insist...

Have GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04. 
Display command doesn't work at all. Nothing displayed thought no errors returned. 
Print command works, so at least stdout (or whatever) is OK. 
Am i specific or is it well-known issue?

You most likely have misinterpreted how to use display.

Here is a simplistic c code (loop.c):
```

#include <stdio.h>

int main()
{
    int i = 10;
    while (i--) {
        printf("i = %d\n", i);
    }

    return 0;
}

```

Compiled it using ```
gcc -g loop.c -o loop
```
And here is the dump of my gdb session while using display:
```
gdb loop
GNU gdb (GDB) 7.1-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/kunal/work/tmp/loop...done.
(gdb) b main
Breakpoint 1 at 0x80483ed: file loop.c, line 5.
(gdb) r
Starting program: /home/kunal/work/tmp/loop 

Breakpoint 1, main () at loop.c:5
5           int i = 10;
(gdb) display /th &i
1: x/th &i  0xbffff78c: 0001111111110100
(gdb) n
6           while (i--) {
1: x/th &i  0xbffff78c: 0000000000001010
(gdb) 
7               printf("i = %d\n", i);
1: x/th &i  0xbffff78c: 0000000000001001
(gdb) 
i = 9
6           while (i--) {
1: x/th &i  0xbffff78c: 0000000000001001
(gdb) display
1: x/th &i  0xbffff78c: 0000000000001001
(gdb) n
6           while (i--) {
1: x/th &i  0xbffff78c: 0000000000001010
(gdb) 
7               printf("i = %d\n", i);
1: x/th &i  0xbffff78c: 0000000000001001
(gdb) 
i = 9
6           while (i--) {
1: x/th &i  0xbffff78c: 0000000000001001
(gdb) display
1: x/th &i  0xbffff78c: 0000000000001001
(gdb) n
7               printf("i = %d\n", i);
1: x/th &i  0xbffff78c: 0000000000001000
(gdb) 
i = 8
6           while (i--) {
1: x/th &i  0xbffff78c: 0000000000001000
(gdb) 
7               printf("i = %d\n", i);
1: x/th &i  0xbffff78c: 0000000000000111
(gdb) 
i = 7
6           while (i--) {
1: x/th &i  0xbffff78c: 0000000000000111
(gdb) 

```

As you can see, every time the debugger stops the program, the display command is executed.

HTH ;)

PS: It helps if you post exactly the command(s) you've tried.
Just saying "Display command doesn't work at all" is of no help.

---

### Post by icegood on 2012-07-27
> **the_unforgiven said:**
> You most likely have misinterpreted how to use display...
No, i'm not. And i've been using it for a ~4 years and all time liked how it works. But for now in new kubuntu i have a problem. Display output is NOTHING.
```

(gdb) p PocketMoleculesLastIndex-PocketMoleculesActiveIndex
$1 = 1
(gdb) display PocketMoleculesLastIndex-PocketMoleculesActiveIndex
(gdb) 

```

So i asked: WTF going on???

---

### Post by dwhitney67 on 2012-07-27
@ icegood

For starters, let me state that you have chosen a good "ubuntu" release.  I also use Kubuntu 12.04 (and previously 11.10), and I'm quite pleased with it.

As for the GDB issue, I cannot duplicate the anomaly that you described.  Of course, I'm testing with very simple code that is contained within a single module.

Do you think you could post a simple program that I can use to mimic the issue you described when you are debugging the program?  Also, it would be helpful to see how you are compiling this program.


P.S.  Here's the simple program I tested with (as seen from within gdb):
```

gdb ./a.out
GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /home/dwhitney67/a.out...done.
(gdb) b main
Breakpoint 1 at 0x4004fc: file foo.c, line 5.
(gdb) l
1	#include <stdio.h>
2	
3	int main()
4	{
5	    const int y = 2;
6	
7	    for (int i = 0; i < 10; ++i)
8	    {
9	        printf("%d x %d is %d\n", i, y, i * y);
10	    }
(gdb) r
Starting program: /home/dwhitney67/a.out 

Breakpoint 1, main () at foo.c:5
5	    const int y = 2;
(gdb) n
7	    for (int i = 0; i < 10; ++i)
(gdb) n
9	        printf("%d x %d is %d\n", i, y, i * y);
(gdb) p i
$1 = 0
(gdb) **display i**
**1: i = 0**
(gdb) n
0 x 2 is 0
7	    for (int i = 0; i < 10; ++i)
**1: i = 0**
(gdb) 

```

---

### Post by icegood on 2012-07-27
foubd that anomality: i compiled with -ggdb option. With it doesn't work. With simply -g everything is OK.
> 
-ggdb
           Produce debugging information for use by GDB.  This means to use the most expressive format available (DWARF 2, stabs, or the native format if neither of those are supported), including GDB extensions if at all possible.

Oh yeah, i obtained really most expressive output!

---

