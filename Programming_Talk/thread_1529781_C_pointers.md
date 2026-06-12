---
title: "C pointers"
date: 2010-07-12
forum: Programming Talk
---

### Post by kyp12 on 2010-07-12
Hi there,
 
I'm using the MS SFU 3.5 (Interix) environment on Windows XP with gcc 3.3. I've written a simple program as a refresher on pointers in C. It compiles and links with no warnings but executes with a memory fault.
 
```
 
#include <stdio.h>
#include <string.h>
char *rmv(char *str);
int main(void) {
        char *pj = "$abc$";
        char *p;
        printf("%s\n", pj);
        p = rmv(pj);
        printf("%s\n", p);
        return 0;
}
char *rmv(char *str) {
        char *ptr;
        if ((ptr = strchr(str, '$')) != NULL)
        {
                str = ptr + 1;
        }
        if ((ptr = strchr(str, '$')) != NULL)
        {
                *ptr = '\0';
        }
        return(str);
}

```
 
 
$ gcc -g -Wall -o test test.c
$ ./test
$abc$
Memory fault (core dumped)
$
 
I've used gdb to attempt some de-bugging and it appears the issue lies with the pointer dereferencing i.e. *ptr = '\0'; I believe that ptr should be pointing to a valid area of memory and gdb confirms this. I am also able to obtain the value of ptr is pointing to before the de-reference ie. gdb> p *ptr. I'm fairly sure the above program would work in native Unix or Posix.
 
```
 
$ gdb ./test
GNU gdb 2002-11-11-cvs
Copyright 2002 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i586-pc-interix3"...
(gdb) break main
Breakpoint 1 at 0x40151e: file test.c, line 8.
(gdb) run
Starting program: /dev/fs/C/Documents and Settings/Mr Paraskevas/test/test
Breakpoint 1, main () at test.c:8
8               char *pj = "$abc$";
(gdb) s
11              printf("%s\n", pj);
(gdb) s
$abc$
12              p = rmv(pj);
(gdb) p pj
$1 = 0x404000 "$abc$"
(gdb) s
rmv (str=0x404000 "$abc$") at test.c:22
22              if ((ptr = strchr(str, '$')) != NULL)
(gdb) s
24                      str = ptr + 1;
(gdb) p ptr
$2 = 0x404000 "$abc$"
(gdb) p str
$3 = 0x404000 "$abc$"
(gdb) s
27              if ((ptr = strchr(str, '$')) != NULL)
(gdb) p ptr
$4 = 0x404000 "$abc$"
(gdb) p str
$5 = 0x404001 "abc$"
(gdb) s
29                      *ptr = '\0';
(gdb) p *ptr
$6 = 36 '$'
(gdb) p ptr
$7 = 0x404004 "$"
(gdb) p str
$8 = 0x404001 "abc$"
(gdb) s
procfs:4284 -- child stopped for unknown reason:
PR_FAULTED : Incurred a traced hardware fault Unknown hardware fault 14
... giving up...

```
 
Any help on this issue would be greatly appreciated.
 
Thanks.

---

### Post by GeneralZod on 2010-07-12
I'm fairly sure that attempting to alter a string literal yields undefined behaviour (in this case, a crash).

---

### Post by kyp12 on 2010-07-12
I can confirm that the above snipett of code (in a much larger context), specifically the altering of the string literal does work on native VMS running a posix shell.

---

### Post by GeneralZod on 2010-07-12
Nonetheless, it's definitely undefined behaviour:

[quote=ANSI C]

6.4.5.6

If the program attempts to modify such an array, the behaviour is
unde&#64257;ned.
[/quote]

"undefined" means precisely that: examples of undefined behaviour are crashing, doing nothing, or even - conceivably - monkeys flying out of your nose :)

---

### Post by Can+~ on 2010-07-12
Instead of:

```
char *pj = "$abc$";
```

Do: 

```
char pj[] = "$abc$";
```

It has to do on how the compiler handles memory assignment. The former creates an initialized read-only string, whereas, the later, creates a read/write string. (I'm not 100% sure about this, though)

---

### Post by trent.josephsen on 2010-07-12
The intention is that
```
char *p = "some string";
```
can store the string in the read-only portion of the program's available memory, and merely initialize p as a pointer into that segment; whereas
```
char p[] = "some string";
```
allocates memory for the array and copies the contents of the string into it (presumably at run time).  You stumbled across one of the implications of this, which is that the *p form can't be written to without invoking undefined behavior.  Another is that two pointers initialized to equivalent string literals might point to the same place; e.g.
```
#include <stdio.h>
int main(void)
{
        char *s = "foo";
        char *t = "foo";
        printf("%p =? %p\n", (void *)s, (void *)t);
}
```
tells me that s and t point to the same location.  This could not happen if s and t were declared as arrays.

When you use a form like char *p = "something", you may want to use **const** so that the compiler can warn you:
```
char const *pj = "$abc$";
```
would have caused the invocation rmv(pj) to raise a warning at compilation.

---

### Post by kyp12 on 2010-07-13
Thanks for that guys really appreciate it.

I just found it strange that the same code executes with no problem on  a DEC VAX machine running native VMS with a posix shell.

---

### Post by Npl on 2010-07-13
you should always compile (atleast newly written) code with the -Wall option.
The compiler will warn you if you cast away the constness of a pointer in the line```
char *pj = "$abc$";
```

correct would be
```
const char *pj = "$abc$";
```
notifying that you cant write to the area referenced by pj (in a usefull and defined way).. and then you would get the same warning at the rmv call. That way you should be forced to write code thats portable and doesn't just run by luck on a few platforms.

---

### Post by trent.josephsen on 2010-07-13
> **kyp12 said:**
> Thanks for that guys really appreciate it.

I just found it strange that the same code executes with no problem on  a DEC VAX machine running native VMS with a posix shell.

Well, one of the worst kinds of "undefined behavior" is doing what you expect.  It can lead you into thinking that there's nothing wrong with the program, and then encountering new and sometimes bizarre problems when you attempt to port it to a system where the assumption you first made doesn't hold.  Looks like you found that out the hard way.

Interesting, though.  I wonder whether you could exploit the behavior of the VAX to do something like this:

```

#include <stdio.h>
int main(void)
{
    char *s = "foo";
    char *t = "foo";
    s[0] = 'm';
    printf("%s\n%s\n", s, t);
}
```
If the VAX recognizes that s and t point to equivalent strings, it might initialize them to the same address, as GCC did on Linux -- but the assignment will then change both at once, and both strings will print as "moo".  On the other hand, the compiler would also be perfectly within its rights to cause demons to fly out of your nose, so this isn't really practical.

@Npl:  The warning will only occur if you're compiling with g++.  In C (not C++) the type of a string literal is "char *", not "char const *".  (Edit:  -Wwrite-strings will treat string literals like C++ does, which is probably a good idea, but might be considered a violation of the C standard.)

---

