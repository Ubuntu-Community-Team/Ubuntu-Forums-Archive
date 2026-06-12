---
title: "help with output in gas assembly"
date: 2009-07-28
forum: Programming Talk
---

### Post by anzac1942 on 2009-07-28
I recently started learning assembly under ubuntu 9.04, using the GNU Assembler and the linker provided with binutils. Everything has gone well so far, but I've run into a few problems with this program and cannot figure out what is wrong. If anybody can help with this, I would appreciate it.

```

#program to sort through a list of numbers and display the largest one... written for gas
.section .data
numbers:[INDENT].int 10, 30, 15, 45, 205, 64
[/INDENT].section .text
.globl _start
_start:[INDENT]movl numbers, %ebx
movl $1, %edi
[/INDENT]loop:[INDENT]movl numbers(, %edi, 4), %eax
cmp %ebx, %eax
cmova %eax, %ebx
inc %edi
cmp $6, %edi
jne loop
movl %ebx, %ecx
movl $4, %eax
movl $1, %ebx
movl $4, %edx #i assumed 32-bit int here
int $0x80
movl $1, %eax
movl $0, %ebx
int $0x80
[/INDENT]
```When I run the linked executable, nothing is output on the screen. The output works fine with .ascii data, but when I try to output a .int like this, nothing is displayed. I have run this through gdb a few times, and all the right values are being moved to the right places at the right times, etc., but still nothing is written to stdout.:confused:

---

