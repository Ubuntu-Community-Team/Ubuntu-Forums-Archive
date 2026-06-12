---
title: "[SOLVED] Might be a bug of scandir()"
date: 2008-01-04
forum: Programming Talk
---

### Post by fyplinux on 2008-01-04
I  am programming under Ubuntu 7.10

sometimes, after scandir(), the  parameter char *dir 's value might be changed.
e.g., my situation was:

before call: dir="a"
after call: dir="a!"

But, when I encountered this problem, *dir is not const, while it is documented that dir is a const value.I dont know if dir is a const, will there still be the problem?

---

### Post by stroyan on 2008-01-04
It is very unlikely that scandir is directly overwriting the value of *dir.  It is more common for the change in value to be caused by a buffer overflow or a memory management error that causes some memory location to be allocated with malloc and freed with free or realloc but still be in use.  That can cause a variable to change value for a most unexpected reason.
I would use gdb and put a watchpoint on the value of "dir" and "*dir" as a dereference of an address. That would show the exact source line or instruction that overwrote "dir" or "*dir". The code that overwrites a variable may not be a guilty party. It could be an innocent victim of previous malloc/free mistakes or insufficient buffer sizes.  But it will at least be a big clue as to what went wrong.

Here is a small example that you can use to get a feel for this debugging tactic. The watchpoint is set as a hex constant instead of "token" or "*&token" so that the expression "watch *(char **)0xbf97f884" will be valid to gdb even when executing in code that has no definition for "token" or even no debuggable source code.```
$ cat strtok.c 
#include <string.h>
#include <stdio.h>
main()
{
        char string[] = "wor\nds sepa,rat\ned by spa\nces -- and, punc:tuation!";
        char* pString = string;
        // const char delimiters[] = "\n";
        // char delimiters = '\n';
        char *token;
        char *null = NULL;

        token = strsep (&pString,"\n");  /* token => "words" */
        while((token=strsep(&pString,"\n"))!=NULL){
                printf("%s\n",token);
        }
}
$ gdb
(gdb) b main
Breakpoint 1 at 0x8048415: file strtok.c, line 4.
(gdb) r
Starting program: /home/mike/a.out 

Breakpoint 1, main () at strtok.c:4
4       {
(gdb) p/a &token
$1 = 0xbf97f884
(gdb) watch *(char **)0xbf97f884
Hardware watchpoint 2: *(char **) 3214407812
(gdb) c
Continuing.
Hardware watchpoint 2: *(char **) 3214407812

Old value = 0x0
New value = 0xbf97f88c "wor"
main () at strtok.c:13
13              while((token=strsep(&pString,"\n"))!=NULL){
```
You can get more information about what is going on inside of scandir by installing and using a debug version of libc.  Use "apt-get install libc6-dbg" and "export LD_LIBRARY_PATH=/usr/lib/debug".

---

