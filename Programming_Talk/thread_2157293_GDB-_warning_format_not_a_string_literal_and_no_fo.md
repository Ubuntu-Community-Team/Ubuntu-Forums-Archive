---
title: "GDB- warning: format not a string literal and no format arguments"
date: 2013-06-24
forum: Programming Talk
---

### Post by theRandy on 2013-06-24
Not sure if this is the right place to post, sorry if it isn't. Im going through a couple of ethical hacking books before i start my CEH ethical hacking course in a few months and one of the things i need to do is examine the registers. Im using a small piece of code in GDB to do so:

```
#include <stdio.h>
#include <string.h>

int main() {
    char str_a[20];
    
    strcpy(str_a, "Hello, world!\n");
    printf(str_a);
}
```

When i compile it using GCC i get the error message - warning: format not a string literal and no format arguments
And when i set a breakpoint on the strcpy line i get a message :
 Function "strcpy" not defined. Make breakpoint pending on future shared library load? (y or [n]) y
Which i assumed would happen as its strcpy is part of a shared library, i also assumed that when i ran it using GDB it would resolve the issue, but it didnt it just skipped that breakpoint altogether and continued onto the next breakpoint.

```
(gdb) list
1    #include <stdio.h>
2    #include <string.h>
3    
4    int main() {
5        char str_a[20];
6        
7        strcpy(str_a, "Hello, world!\n");
8        printf(str_a);
9    }(gdb) break 6
Breakpoint 1 at 0x4005fb: file char_array2.c, line 6.
(gdb) break strcpy
Function "strcpy" not defined.
Make breakpoint pending on future shared library load? (y or [n]) y

Breakpoint 2 (strcpy) pending.
(gdb) break 8
Breakpoint 3 at 0x400614: file char_array2.c, line 8.
(gdb) run
Starting program: /root/Documents/Programming/char_array2 

Breakpoint 1, main () at char_array2.c:7
7        strcpy(str_a, "Hello, world!\n");
(gdb) i r rip
rip            0x4005fb    0x4005fb <main+23>
(gdb) x/5i $rip
=> 0x4005fb <main+23>:    mov    ecx,0x40072c
   0x400600 <main+28>:    lea    rax,[rbp-0x20]
   0x400604 <main+32>:    mov    edx,0xf
   0x400609 <main+37>:    mov    rsi,rcx
   0x40060c <main+40>:    mov    rdi,rax
(gdb) continue
Continuing.

Breakpoint 3, main () at char_array2.c:8
8        printf(str_a);
(gdb) i r rip
rip            0x400614    0x400614 <main+48>
(gdb) x/5i $rip
=> 0x400614 <main+48>:    lea    rax,[rbp-0x20]
   0x400618 <main+52>:    mov    rdi,rax
   0x40061b <main+55>:    mov    eax,0x0
   0x400620 <main+60>:    call   0x4004b8 <printf@plt>
   0x400625 <main+65>:    mov    rdx,QWORD PTR [rbp-0x8]
(gdb) continue
Continuing.
Hello, world!

```

Anyone know what i did wrong?

---

### Post by oldos2er on 2013-06-24
Moved to Programming Talk.

---

### Post by Bachstelze on 2013-06-25
About the warning, you should not do things like

```
char *s;
/* Some code... */
printf(s);
```

Instead, do

```
printf("%s", s);
```

About the message in gdb, you should do 'break 7' to break on line 7 of your program. If you do 'break function', it will break *after* the call to the function (so inside its body). Since at the time you run gdb, it does not know what's inside strcpy(), you get that message. So just do 'break 7', you probably don't want to know what's inside strcpy() anyway.

---

### Post by theRandy on 2013-06-25
Ahh ok, I wrote the code exactly how it was shown in the Hacking: The art of exploitation book. Your break 7 method worked but i found that you can put a break-point on strcpy() by compiling it with the GCC compiler using the fno-builtin command, and it gives no errors.

```
root@bt:~/Documents/Programming# gcc -fno-builtin -g char_array2.c
root@bt:~/Documents/Programming# l -ls a.out
12 -rwxr-xr-x 1 root root 9929 2013-06-26 12:22 a.out*
root@bt:~/Documents/Programming# ./a.out
Hello, world!
root@bt:~/Documents/Programming# gdb -q a.out
Reading symbols from /root/Documents/Programming/a.out...done.
(gdb) list
1    #include <stdio.h>
2    #include <string.h>
3    
4    int main() {
5        char str_a[20];
6        
7        strcpy(str_a, "Hello, world!\n");
8        printf(str_a);
9    }(gdb) break 6
Breakpoint 1 at 0x4005fb: file char_array2.c, line 6.
(gdb) break strcpy
Breakpoint 2 at 0x4004e8
(gdb) break 8
Breakpoint 3 at 0x40060f: file char_array2.c, line 8.
(gdb) run
Starting program: /root/Documents/Programming/a.out 

Breakpoint 1, main () at char_array2.c:7
7        strcpy(str_a, "Hello, world!\n");
(gdb) i r rip
rip            0x4005fb    0x4005fb <main+23>
(gdb) x/5i $rip
=> 0x4005fb <main+23>:    mov    edx,0x40072c
   0x400600 <main+28>:    lea    rax,[rbp-0x20]
   0x400604 <main+32>:    mov    rsi,rdx
   0x400607 <main+35>:    mov    rdi,rax
   0x40060a <main+38>:    call   0x4004e8 <strcpy@plt>
(gdb) continue
Continuing.

Breakpoint 2, 0x00007ffff7adb060 in strcpy () from /lib/libc.so.6
(gdb) i r rip
rip            0x7ffff7adb060    0x7ffff7adb060 <strcpy>
(gdb) x/5i $rip
=> 0x7ffff7adb060 <strcpy>:    
    cmp    DWORD PTR [rip+0x301139],0x0        # 0x7ffff7ddc1a0
   0x7ffff7adb067 <strcpy+7>:    jne    0x7ffff7adb06e <strcpy+14>
   0x7ffff7adb069 <strcpy+9>:    call   0x7ffff7a76000
   0x7ffff7adb06e <strcpy+14>:    lea    rax,[rip+0x1b]        # 0x7ffff7adb090
   0x7ffff7adb075 <strcpy+21>:    
    test   DWORD PTR [rip+0x301131],0x200        # 0x7ffff7ddc1b0
(gdb) continue
Continuing.

Breakpoint 3, main () at char_array2.c:8
8        printf(str_a);
(gdb) i r rip
rip            0x40060f    0x40060f <main+43>
(gdb) x/5i $rip
=> 0x40060f <main+43>:    lea    rax,[rbp-0x20]
   0x400613 <main+47>:    mov    rdi,rax
   0x400616 <main+50>:    mov    eax,0x0
   0x40061b <main+55>:    call   0x4004b8 <printf@plt>
   0x400620 <main+60>:    mov    rdx,QWORD PTR [rbp-0x8]
(gdb) 

```

Thanks for the help.

---

### Post by Bachstelze on 2013-06-26
In this case, doing printf(str) is okay because you know what str contains. However if str may contain arbitrary data (typically supplied by the user), then you should always do printf("%s", str) to prevent format-string-based attacks (Google it if you are interested, but the book you are reading covers them as well).

And yes, looking at it more closely, when you compile your code with the default settings, strcpy() is not called at all (instead, your program performs the same operation using raw CPU instructions). Using -fno-builtin prevents such optimisations, so the call to strcpy() is there as expected.

(Also, normally I should say that you really should get used as soon as possible to using at least strncpy() instead of strcpy(), but you will see that soon enough in the book.)

---

