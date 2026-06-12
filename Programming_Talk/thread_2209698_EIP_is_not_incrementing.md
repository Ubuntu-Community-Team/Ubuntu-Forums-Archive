---
title: "EIP is not incrementing"
date: 2014-03-06
forum: Programming Talk
---

### Post by sveltepumpkin on 2014-03-06
I'm following through examples in the book, The Art of Exploitation by Jon Erickson. For some reason when I try to increment the program in gdb the address of the EIP register does not increment. It's using an old version of Ubuntu.

The output from gdb is ```
svelte@pumpkin:~/booksrc $ gdb -q ./a.out
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb) break main
Breakpoint 1 at 0x8048384: file firstprog.c, line 6.
(gdb) disassemble main
Dump of assembler code for function main:
0x08048374 <main+0>:    push   ebp
0x08048375 <main+1>:    mov    ebp,esp
0x08048377 <main+3>:    sub    esp,0x8
0x0804837a <main+6>:    and    esp,0xfffffff0
0x0804837d <main+9>:    mov    eax,0x0
0x08048382 <main+14>:   sub    esp,eax
0x08048384 <main+16>:   mov    DWORD PTR [ebp-4],0x0
0x0804838b <main+23>:   cmp    DWORD PTR [ebp-4],0x9
0x0804838f <main+27>:   jle    0x8048393 <main+31>
0x08048391 <main+29>:   jmp    0x80483a6 <main+50>
0x08048393 <main+31>:   mov    DWORD PTR [esp],0x8048484
0x0804839a <main+38>:   call   0x80482a0 <printf@plt>
0x0804839f <main+43>:   lea    eax,[ebp-4]
0x080483a2 <main+46>:   inc    DWORD PTR [eax]
0x080483a4 <main+48>:   jmp    0x804838b <main+23>
0x080483a6 <main+50>:   leave  
0x080483a7 <main+51>:   ret    
End of assembler dump.
(gdb) run
Starting program: /home/svelte/booksrc/a.out 

Breakpoint 1, main () at firstprog.c:6
6         for(i=0; i < 10; i++)
(gdb) info register $eip
eip            0x8048384        0x8048384 <main+16>
(gdb) nexti
6         for(i=0; i < 10; i++)
(gdb) info register $eip
eip            0x8048384        0x8048384 <main+16>
(gdb) nexti
6         for(i=0; i < 10; i++)
(gdb) info register eip
eip            0x8048384        0x8048384 <main+16>
(gdb) next

Breakpoint 1, main () at firstprog.c:6
6         for(i=0; i < 10; i++)
(gdb) info register eip
eip            0x8048384        0x8048384 <main+16>
(gdb) list
1       #include <stdio.h>
2
3       int main()
4       {
5         int i;
6         for(i=0; i < 10; i++)
7         {
8           printf("Hello World!\n");
9         }
10      }
(gdb) 


```

---

### Post by Bachstelze on 2014-03-08
Hmm, it shouldn't do that, and I can't run the Live CD right now as my laptop's drive seems broken... In any case, as you said the version of Ubuntu in the provided Live CD is very old, so if I were you I would copy the code over to a more recent system and work from there, you will just have to tweak some minor settings and/or use some additional compilation flags to make most things work.

---

