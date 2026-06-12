---
title: "HELP!! Assembly code"
date: 2012-09-27
forum: Programming Talk
---

### Post by YuKill on 2012-09-27
So, i was coding in assembly (IAS-32), when i got an arithmetical error. I searched over and over but couldnt figure it out. I dont know why but when I try to do 2/1, this error pops out. The problem is, I have to finish it today, so... any help will be good =D 
Here is the code:

```

.section .data
    mat:
        .int 1,3,7,2

.section .bss
    .lcomm mat1, 40

.section .text


.globl _start
_start:
    nop
    movl $0, %ecx

    calcDet:
    movl mat(,%ecx,4), %eax
    add $2, %ecx
    movl mat(,%ecx,4), %ebx
    mul %ebx
    cmp $3, %ecx
    je inverte
    pushl %eax
    dec %ecx
    jmp calcDet
    
    inverte:
    pop %ebx
    sub %eax, %ebx
    movl $0, %ecx

    diagPrin:
    movl mat(,%ecx,4), %eax
    cmp $0, %eax
    je gamb3
    div %ebx
    
    gamb3:
    cmp $2, %ecx
    je executa
    add $2, %ecx
    movl %eax, mat1(,%ecx,4)
    jmp diagPrin

    executa:
    sub $2, %ecx
    movl %eax, mat1(,%ecx,4)
    inc %ecx

    inverteSinal:
    movl mat(,%ecx,4), %eax
    cmp $0, %eax    
    je gamb
    div %ebx
    
    gamb:
    movl $-1, %edx
    mul %edx
    movl %eax, mat1(,%ecx,4) 
    add $2, %ecx
    movl mat(,%ecx,4), %eax
    cmp $0, %eax
    je gamb2
    div %ebx   <-----------------------------ERROR

    gamb2:
    mul %edx
    movl %eax, mat1(,%ecx,4)
    
    
fim:
    movl $1, %eax
    movl $0, %ebx
    int $0x80

```PS: This code tries to do the inverse of the matrix {1,3,7,2} 
l    1        3      l
              l     2       7      l

---

### Post by Zugzwang on 2012-09-27
Did you try debugging your program. My guess is that ebx has a value of 0 at the time of execution, so you are dividing by 0. By step-by-step executing your program, you will see where such a value comes from.

---

### Post by YuKill on 2012-09-27
I thought that so.... but when i ran gdb, it comes out that ebx is 1

(gdb) 
60        add $2, %ecx
(gdb) 
61        movl mat(,%ecx,4), %eax
(gdb) 
62        cmp $0, %eax
(gdb) 
63        je gamb2
(gdb) 
64        div %ebx
(gdb) p $ebx
$1 = 1

---

### Post by ofnuts on 2012-09-27
> **YuKill said:**
> I thought that so.... but when i ran gdb, it comes out that ebx is 1

(gdb) 
60        add $2, %ecx
(gdb) 
61        movl mat(,%ecx,4), %eax
(gdb) 
62        cmp $0, %eax
(gdb) 
63        je gamb2
(gdb) 
64        div %ebx
(gdb) p $ebx
$1 = 1
Very hazy memory, so I'm shooting in the dark, but since you are  likely using signed numbers, shouldn't you be using IDIV (and IMUL) instead of DIV? Maybe the complaint is about EDX/EAX contents, btw.

---

### Post by xb12x on 2012-09-27
Are you running the code on a PC as a user logged into an O.S. such as Ubuntu or Windows? If so, the x86-style CPU is running in 'Protected Mode' and your code is running in 'Userland'.  

What you're trying to do requires direct access to the hardware and modern O.S.'s try their best to prevent that from happening from Userland.

A simple way to get direct access to your PC's hardware in order to  play with assembly code is to boot a 'Real-Mode' O.S. such as DOS (and get a DOS assembler, linker, etc).

Or write kernel-level code (drivers, etc).

---

### Post by YuKill on 2012-09-27
Well, I'm running at Ubuntu. I wouldn't get this error if I couldn't access the hardware of my computer, would I? So, I dont think the code is wrong... if I change the vector(mat) to 1,0,1,0 it works just fine...

Still lossst....

---

### Post by trent.josephsen on 2012-09-27
> **YuKill said:**
> Well, I'm running at Ubuntu. I wouldn't get this error if I couldn't access the hardware of my computer, would I?

[QUOTE=RinkWorks.com]A man attempting to set up his new printer called the printer's tech support number, complaining about the error message: "Can't find the printer." On the phone, the man said he even held the printer up in front of the screen, but the computer still couldn't find it. [/QUOTE]

Analogous mistake. You as a computer user may have access to the hardware, but you as a programmer still can't necessarily "access" the hardware. There are protection mechanisms in place to prevent (unelevated) direct hardware access, which is what xb12x is talking about.

However, I'm not sure that's your real problem. My x86 really isn't up to snuff anymore (it never really was), but...

Am I mistaken in guessing that when you ran in the debugger, it didn't cause the error? You didn't show that part of the debugging session. If that's the case, you probably have some very subtle bug in another part of your program. Assembly, man, it's awful for that.

---

### Post by YuKill on 2012-09-27
Nope, in the debugger I get the same error... =/

---

### Post by Zugzwang on 2012-09-27
> **YuKill said:**
> Nope, in the debugger I get the same error... =/

Ok, then run your program step-by-step until you hit the error and post us the output. Your GDB log is too short - it ends before the error occurs. Show us all the register contents right one command before the error.

---

### Post by YuKill on 2012-09-27
Actually, if a I press enter one more time, the error pops out which means that it doesnt execute the division or it simply (but not as simply as it seems) doesnt do that! D=

13        nop
(gdb) n
14        movl $0, %ecx
(gdb) 
17        movl mat(,%ecx,4), %eax
(gdb) 
18        add $2, %ecx
(gdb) 
19        movl mat(,%ecx,4), %ebx
(gdb) 
20        mul %ebx
(gdb) 
21        cmp $3, %ecx
(gdb) 
22        je inverte
(gdb) 
23        pushl %eax
(gdb) 
24        dec %ecx
(gdb) 
25        jmp calcDet
(gdb) 
17        movl mat(,%ecx,4), %eax
(gdb) 
18        add $2, %ecx
(gdb) 
19        movl mat(,%ecx,4), %ebx
(gdb) 
20        mul %ebx
(gdb) 
21        cmp $3, %ecx
(gdb) 
22        je inverte
(gdb) 
28        pop %ebx
(gdb) 
29        sub %eax, %ebx
(gdb) 
30        movl $0, %ecx
(gdb) 
33        movl mat(,%ecx,4), %eax
(gdb) 
34        cmp $0, %eax
(gdb) 
35        je gamb3
(gdb) 
36        div %ebx
(gdb) 
39        cmp $2, %ecx
(gdb) 
40        je executa
(gdb) 
41        add $2, %ecx
(gdb) 
42        movl %eax, mat1(,%ecx,4)
(gdb) 
43        jmp diagPrin
(gdb) 
33        movl mat(,%ecx,4), %eax
(gdb) 
34        cmp $0, %eax
(gdb) 
35        je gamb3
(gdb) 
36        div %ebx
(gdb) 
39        cmp $2, %ecx
(gdb) 
40        je executa
(gdb) 
46        sub $2, %ecx
(gdb) 
47        movl %eax, mat1(,%ecx,4)
(gdb) 
48        inc %ecx
(gdb) 
51        movl mat(,%ecx,4), %eax
(gdb) 
52        cmp $0, %eax    
(gdb) 
53        je gamb
(gdb) 
54        div %ebx
(gdb) 
57        movl $-1, %edx
(gdb) 
58        mul %edx
(gdb) 
59        movl %eax, mat1(,%ecx,4) 
(gdb) 
60        add $2, %ecx
(gdb) 
61        movl mat(,%ecx,4), %eax
(gdb) 
62        cmp $0, %eax
(gdb) 
63        je gamb2
(gdb) 
64        div %ebx
(gdb) 

Program received signal SIGFPE, Arithmetic exception.
gamb () at InvMatriz.s:64
64        div %ebx

---

### Post by ofnuts on 2012-09-28
Still doesn't tell us the contents of EAX, EDX, and EBX before the DIV (maybe it could be deduced from the code, but we have better things to do...)

Also, integer inversion of matrices of integers is a new concept to me... Normally you end up with non integer values. This code could work on this very matrix (its inverse is also all integers) but it won't work in the general case.

And the result contains negative values, so I persist on my recommendation to use imul/idiv.

---

### Post by xb12x on 2012-09-29
Are you running this 32-bit code on a 64-bit version of Linux? If so, how did you build it?

---

### Post by jwbrase on 2012-09-29
> **xb12x said:**
> Are you running the code on a PC as a user logged into an O.S. such as Ubuntu or Windows? If so, the x86-style CPU is running in 'Protected Mode' and your code is running in 'Userland'.  

What you're trying to do requires direct access to the hardware and modern O.S.'s try their best to prevent that from happening from Userland.

A simple way to get direct access to your PC's hardware in order to  play with assembly code is to boot a 'Real-Mode' O.S. such as DOS (and get a DOS assembler, linker, etc).

Or write kernel-level code (drivers, etc).

I think you're a bit confused about assembly code and direct hardware access. Just because you're writing assembly code does *not* mean that you're accessing the hardware directly, and I don't see any hardware access instructions in the OP's code.

Direct hardware access is usually done with assembly code because it depends on machine-specific things that generally aren't exposed in higher level languages like C, but you can write assembly code that doesn't do direct hardware access and will run under a protected-mode operating system. (In fact, assembly code is just a human readable representation of the machine code that *all* compiled executables are made up of).

---

### Post by jwbrase on 2012-09-29
I tried assembling and running the program myself, and I get the same error.

Immediately before the SIGFPE, the register contents are:

```
(gdb) info registers
eax            0x2	2
ecx            0x3	3
edx            0x2	2
ebx            0x1	1
esp            0xffffd880	0xffffd880
ebp            0x0	0x0
esi            0x0	0
edi            0x0	0
eip            0x80480f3	0x80480f3 <gamb+29>
eflags         0x202	[ IF ]
cs             0x23	35
ss             0x2b	43
ds             0x2b	43
es             0x2b	43
fs             0x0	0
gs             0x0	0

```

---

### Post by trent.josephsen on 2012-09-29
Thanks to jwbrase's debugger output and [this wikibook page](http://en.wikibooks.org/wiki/X86_Assembly/Arithmetic) (not to mention having nothing else to do), I figured it out:

> If quotient does not fit into quotient register, arithmetic overflow interrupt occurs.

Makes sense. You're dividing the 64 bit dividend EDX:EAX by EBX, so when EDX and EAX are both 2, you're dividing the 64-bit number 0x0000000200000002 (decimal 8589934594) by 0x00000001. The DIV operation is supposed to put the 32-bit quotient in EAX (and the 32-bit remainder in EDX), but the quotient is 0x200000002, which won't fit in a 32 bit register. So the instruction causes an interrupt, which in turn results in SIGFPE.

Simple! :lol:

---

### Post by xb12x on 2012-09-29
> **jwbrase said:**
>  Just because you're writing assembly code does *not* mean that you're accessing the hardware directly, and I don't see any hardware access instructions in the OP's code..

You are absolutely correct,  in general, but not in this case.

From your posting of the gdb register dump, look at EDX:EAX and EBX.  The  failure is not because EBX is zero, but because EDX:EAX is ........  and  EBX is ........ 

Hint: It's running on a modern O.S.

Trent, nice catch!

---

### Post by xb12x on 2012-09-29
gamb:
    movl $-1, %edx
    mul %edx

Negative numbers are represented by the two's complement. So EDX contains 0xFFFFFFFF after this instruction.

In Python this would not be a problem. In C/C++ the compiler would warn you, or possibly fail with an error.

And with today's optimizing compilers you really can't do much better by hand. Assembly programming is obsolete.

That is why I see no need anymore for anybody to learn assembly programming if doing so to find a job. Anything once done in assembly is now done in 'C', including PC firmware (UEFI replaced the BIOS), drivers, embedded/handheld firmware, etc.

---

### Post by jwbrase on 2012-09-30
> **xb12x said:**
> You are absolutely correct,  in general, but not in this case.

From your posting of the gdb register dump, look at EDX:EAX and EBX.  The  failure is not because EBX is zero, but because EDX:EAX is ........  and  EBX is ........ 

Hint: It's running on a modern O.S.

The OS has nothing to do with it. Load the registers with the same values and execute DIV %ebx and the CPU will throw an INT 0 (divide error) whether you're running in DOS or Linux, protected mode or real mode.

---

### Post by trent.josephsen on 2012-09-30
> **xb12x said:**
> Assembly programming is obsolete.

You are wrong, but it would be a waste of effort on my part to try to change your mind, so I'll leave it at that.

---

