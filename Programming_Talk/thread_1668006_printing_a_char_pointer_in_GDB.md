---
title: "printing a char pointer in GDB"
date: 2011-01-15
forum: Programming Talk
---

### Post by karpay on 2011-01-15
Hi,

I write a code snippet in c++ and I'm trying to debug my program. 
Here &#305;s the code snippet that I wrote:

```


char myStr[] = "Ben bir garip keloglanim.";
char *pch;
pch = strtok(myStr, " ");


```

I compiled this code snippet by the command below:

g++ -g -Wall *.cc -o search


Later on started to debug this code. Below is my terminal history while I was debugging the code:

```

y@y-Ubuntu:~/speechDBSearch$ gdb search
GNU gdb (GDB) 7.2-ubuntu
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/speechDBSearch/search...done.
(gdb) n
The program is not being run.
(gdb) break 4
Breakpoint 1 at 0x8048a9a: file main.cc, line 4.
(gdb) r
Starting program: /home/speechDBSearch/search 
searching program started.

Breakpoint 1, splitTheWord () at main.cc:14
14	{
(gdb) n
15		char myStr[] = "Ben bir garip keloglanim.";
(gdb) 
[COLOR="Red"]
17		pch = strtok(myStr, " ");
(gdb) print pch
$1 = 0x3b4ff4 "|\215\025"[/COLOR]
(gdb) n
18		cout << pch << endl;
(gdb) 
Ben
19	}
(gdb) 
main (argc=1, argv=0xbffff424) at main.cc:43
43		cout << "searching program ended." << endl;
(gdb) 
searching program ended.
44		return 0;
(gdb) 
45	}
(gdb) 
0x00272ce7 in __libc_start_main () from /lib/libc.so.6
(gdb) 
Single stepping until exit from function __libc_start_main,
which has no line number information.

Program exited normally.
(gdb) quit


```


The question is,

I wanted to see the value of the variable "pch" and I used 
"print pch "

command for this purpose. However, dbg did not printed out the value as a char. It displayed some numbers &#305;nstead.

If I want to display the value as a char what should I have to do in gdb?

Any kind of help is kindly appreciated.
Best Regards...

---

### Post by MadCow108 on 2011-01-15
gdb displays the next line to be executed when you do next not the line it already has executed.
So you looked and pch before it was assigned to => it points to garbage (= some numbers)

after the next *next* it should have a value which gdb will display properly

---

### Post by karpay on 2011-01-16
Dear MadCow,

You are right :)

Thanks for the help :)

---

