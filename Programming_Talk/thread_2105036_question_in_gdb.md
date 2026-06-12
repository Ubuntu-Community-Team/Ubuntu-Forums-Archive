---
title: "question in gdb"
date: 2013-01-15
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-15
Hello, 
I wrote this simple program which prints all the arguments given to a program.

My code is straightforward and this is it
```

#include <stdio.h>
#include <malloc.h>

int i = 0;
int main(int argc, char** argv)
{
 printf("\nargc == [%d]",argc);
 printf("\nthe arguments are ");
 for(i=0;i<argc;i++)
 {
  printf("\nargv[%d] == [%s]",i,*(argv+i));
 }

 return 0;
}

```


And this is what I see in gdb
```

argc == [4]
the arguments are 
argv[0] == [/home/Desktop/gdb/five/a.out]
argv[1] == [hello]
argv[2] == [world]
0x00007ffff7a5a30d in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
(gdb) n
Single stepping until exit from function __libc_start_main,
which has no line number information.
argv[3] == [again][Inferior 1 (process 2566) exited normally]

```

My question is :  why is is that only the last argument is printed seperately, like, after a line, though there is nothing in code which tells it to do so ?
Or, is this the way for the last line of every program ?

---

### Post by spjackson on 2013-01-15
Output to stdout, when it is a terminal, is normally line buffered: a whole line is sent to the terminal in one go. The library software does not know that a line is complete until it sees the '\n'. Your last line is not terminated by a newline, so it doesn't get output while main is running.

Among the activities that happen after returning from main is that stdout has its buffer flushed and the file is closed. This is the point at which your last line of output is printed.

Normally people put '\n' at the end of a string rather than the beginning, so the line gets printed there and then. You could do that, or you could output a newline before the return, or call fflush(stdout) at that point.

---

### Post by IAMTubby on 2013-01-15
> **spjackson said:**
> You could do that, or you could output a newline before the return, or call fflush(stdout) at that point.
Wow Sir, what a wonderful explanation :). Thanks a lot.

---

