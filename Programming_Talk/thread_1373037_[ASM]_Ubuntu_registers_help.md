---
title: "[ASM] Ubuntu registers help"
date: 2010-01-05
forum: Programming Talk
---

### Post by lolzwut on 2010-01-05
Hi,


I have a HP G60 Notebook and I'm running Ubuntu 9.04 dual-booted with Windows Vista Home Premium. I just started learning Assembly from some online tutorial, I have basically no knowledge of Assembly. I'm not even sure which one I'm programming in, but I know that the registers I've been learning about are the ones that start with e (eax, ebx, ecx, edx, esi etc.). Anyway in order to understand how to use gdb they said to disassemble this C program:

```
#include<stdio.h> 
#include<stdlib.h> 
 
int add(int x, int y) 
{ 
        int z =10; 
 
        z = x + y; 
        return z; 
} 
 
main(int argc, char **argv) 
{ 
        int a = atoi(argv[1]); 
        int b = atoi(argv[2]); 
        int c; 
        char buffer[100]; 
 
        gets(buffer); 
        puts(buffer); 
 
        c = add(a,b); 
 
        printf("Sum of %d+%d = %d\n",a, b, c); 
 
        exit(0); 
}

```


so I did

me@ubuntu: ~$ gdb ./SimpleDemo
(gdb): disassemble main

then the output I got was:

0x0000000000400676 <main+0>:    push   %rbp
0x0000000000400677 <main+1>:    mov    %rsp,%rbp
0x000000000040067a <main+4>:    push   %rbx
0x000000000040067b <main+5>:    sub    $0x98,%rsp
0x0000000000400682 <main+12>:    mov    %edi,-0x94(%rbp)
0x0000000000400688 <main+18>:    mov    %rsi,-0xa0(%rbp)
0x000000000040068f <main+25>:    mov    %fs:0x28,%rax
0x0000000000400698 <main+34>:    mov    %rax,-0x18(%rbp)
0x000000000040069c <main+38>:    xor    %eax,%eax
0x000000000040069e <main+40>:    mov    -0xa0(%rbp),%rax
0x00000000004006a5 <main+47>:    add    $0x8,%rax
0x00000000004006a9 <main+51>:    mov    (%rax),%rax
0x00000000004006ac <main+54>:    mov    %rax,%rdi
0x00000000004006af <main+57>:    callq  0x400548 <atoi@plt>
0x00000000004006b4 <main+62>:    mov    %eax,-0x84(%rbp)
0x00000000004006ba <main+68>:    mov    -0xa0(%rbp),%rax
0x00000000004006c1 <main+75>:    add    $0x10,%rax
0x00000000004006c5 <main+79>:    mov    (%rax),%rax
0x00000000004006c8 <main+82>:    mov    %rax,%rdi
0x00000000004006cb <main+85>:    callq  0x400548 <atoi@plt>
0x00000000004006d0 <main+90>:    mov    %eax,-0x88(%rbp)
0x00000000004006d6 <main+96>:    lea    -0x80(%rbp),%rax
---Type <return> to continue, or q <return> to quit---gdb ./SimpleDemo


Why are the registers %rax %rdp and stuff? What type of Assembly does Ubuntu even have? I know there's Intel and AT&T syntax but I don't know how to recognize it and I don't know anything about this or why the registers are different. Can someone tell me what ASM the kernel runs? Also can I still program with the regular registers that I'm familiar with? Or will that not work? Thanks.

---

### Post by Zugzwang on 2010-01-05
Looks like you are running the 64-bit version of Ubuntu. In 64-bit mode, 64-bit registers are used, so instead of "eax", "rax" is used. Note that you can still use commands like "xor eax,eax", but they will only operate on the lower 32-bit of the register. Note that "xor eax,eax" is a particularly bad example for this. To get to know why, read an introduction on 64-bit assembly.

If you compile your program with the "-m32" switch, you will obtain a 32-bit executable instead which will not contain 64-bit commands. Maybe this is what you want?

And as far as the syntax is concerned, that's indeed AT&T syntax.

---

### Post by lolzwut on 2010-01-05
Thanks for the useful information.

One question though, the -m32 switch is that for when you compile asm programs or do you use that switch when you compile with gcc?

---

### Post by Zugzwang on 2010-01-05
> **lolzwut said:**
> One question though, the -m32 switch is that for when you compile asm programs or do you use that switch when you compile with gcc?

You use it when compiling with GCC. You probably also need to have the pacakges "ia32-libs" and/or "gcc-multilib" installed in order have the linking process working.

---

### Post by lolzwut on 2010-01-05
Wow, thank you so much. You saved me so much time. I can't thank you enough.

---

### Post by lolzwut on 2010-01-06
I apologize, but I have one last question.

Is there a -m32 switch or something similar for when you compile an ASM program and other compiled languages like Java? Or is it just for C.

Thanks.

---

### Post by Zugzwang on 2010-01-06
For Java, there is no such thing as Java's bytecode is platform-independent and compiled on-the-fly at runtime (or interpreted). 

For the assembler, there's also no such thing, as it doesn't generate code for you. It just assembles the code you write. So there is no need to tell the assembler what kind of code should be generated. *However*, there are instructions for the assembler to tell it in which processor mode (16-bit/32-bit/64-bit) the commands are meant be executed in. I don't know the AT&T ones, but for NASM, it's "BITS 16", "BITS 32" and "BITS 64". These commands are written in the source files, so you also don't provide them as a command line option.

---

