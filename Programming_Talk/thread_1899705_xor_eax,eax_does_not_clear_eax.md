---
title: "xor eax,eax does not clear eax???"
date: 2011-12-24
forum: Programming Talk
---

### Post by das86 on 2011-12-24
Hi, when I try to compile a simple code to check the use of xor in clearing out registers, instead of having the eax become 0, it becomes 0xffffffff.:confused::confused::confused:

---

### Post by Bachstelze on 2011-12-24
Post your code.

---

### Post by Majorix on 2011-12-24
Why not just load your register with 0?

---

### Post by Bachstelze on 2011-12-24
> **Majorix said:**
> Why not just load your register with 0?

Because xor'ing it with itself results in smaller code.

---

### Post by Majorix on 2011-12-24
I would believe that xor'ing your register would have more overhead than just loading it with 0.

Other than that, I believe the OP might just be asking for us to do his homework...

---

### Post by gnometorule on 2011-12-24
If you want other reasons why XOR EAX, EAX is used as opposed to loading 0: in old school overflow attacks, you try to avoid having 0s in your script that you try to inject. Loading 0 into a register has, obviously, a 0 in the script; using XOR doesn't. Maybe that's where the code is from. The overhead isn't larger either.

---

### Post by Bachstelze on 2011-12-24
> **Majorix said:**
> I would believe that xor'ing your register would have more overhead than just loading it with 0.


Then you are wrong.

---

### Post by jwbrase on 2011-12-24
> **Majorix said:**
> I would believe that xor'ing your register would have more overhead than just loading it with 0.

Nope. xor eax,eax is two bytes, mov eax,0 is five. Also, on the original 8086, zeroing eax with xor took 3 clock cycles, while zeroing it with mov took 4. (Timings on modern processors may be different, but the general principle that arithmetic operations between registers are faster than immediate movs will hold).

> 
Other than that, I believe the OP might just be asking for us to do his homework...

I don't see how.

---

### Post by lisati on 2011-12-24
> **Bachstelze said:**
> Post your code.

Agreed. xor'ing a register with itself *should* result in it being zeroed.

---

### Post by das86 on 2011-12-25
> **Majorix said:**
> I would believe that xor'ing your register would have more overhead than just loading it with 0.

Other than that, I believe the OP might just be asking for us to do his homework...

I am self-studying, so it is not homework.

---

### Post by lisati on 2011-12-25
> **das86 said:**
> I am self-studying, so it is not homework.

You've been asked for an example of your code twice. Should I close this thread?

---

### Post by das86 on 2011-12-25
> **lisati said:**
> You've been asked for an example of your code twice. Should I close this thread?
Sorry, my computer got some problem before I could post the code. Here is the code:
section .data

section .text
    global    _start
_start:
    nop

    ;mov eax,1
    xor eax,eax

    nop

As you can see, it is just a simple piece of code. I just wanted to see the result of using xor for clearing a register.

---

### Post by Bachstelze on 2011-12-25
> **das86 said:**
> Sorry, my computer got some problem before I could post the code. Here is the code:
section .data

section .text
    global    _start
_start:
    nop

    ;mov eax,1
    xor eax,eax

    nop

As you can see, it is just a simple piece of code. I just wanted to see the result of using xor for clearing a register.

How do you assemble/run it?

---

### Post by das86 on 2011-12-25
I am using a makefile to compile. Here is the code in the makefile:
sandbox: sandbox.o
    ld -o sandbox sandbox.o
sandbox.o: sandbox.asm
    nasm -f elf -g -F stabs sandbox.asm

In the Konsole, I then type make -k [Enter]. Then I use insight for debugging.

---

### Post by Bachstelze on 2011-12-25
Well, ignoring the fact that this code is obviously useless and not a proper executable, gdb disagrees (I modified the code to make it more obvious that xor works as intended):

```
firas@itsuki ~ % cat test.asm       
section .data

section .text
global _start
_start:
nop

mov eax,12345
mov ebx,eax
xor eax,eax

nop

firas@itsuki ~ % nasm -f elf -g -F stabs test.asm
firas@itsuki ~ % ld -o test test.o 
firas@itsuki ~ % gdb ./test 
GNU gdb (Ubuntu/Linaro 7.3-0ubuntu2) 7.3-2011.08
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /home/firas/test...done.
(gdb) start
Function "main" not defined.
Make breakpoint pending on future shared library load? (y or [n]) n
Starting program: /home/firas/test 

Program received signal SIGSEGV, Segmentation fault.
0x0804806b in ?? ()
(gdb) info register
eax            0x0	0
ecx            0x0	0
edx            0x0	0
ebx            0x3039	12345
esp            0xbffffbe0	0xbffffbe0
ebp            0x0	0x0
esi            0x0	0
edi            0x0	0
eip            0x804806b	0x804806b
eflags         0x10246	[ PF ZF IF RF ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x0	0
(gdb) 

```

---

### Post by das86 on 2011-12-25
It IS a useless piece of code, but all I wanted to do was check the use of xor. I had thought of putting a value in eax like you did, but then isn't xor eax,eax supposed to clear the register whatever value there is in it?
Why does gdb disagree with it?

---

### Post by Arndt on 2011-12-25
> **das86 said:**
> It IS a useless piece of code, but all I wanted to do was check the use of xor. I had thought of putting a value in eax like you did, but then isn't xor eax,eax supposed to clear the register whatever value there is in it?
Why does gdb disagree with it?

Rather than letting the program run until an exception occurs, I put a breakpoint at its start and single stepped. But my results are the same as Bachstelze's: eax becomes 0. How exactly do you determine what the result is?

---

### Post by das86 on 2011-12-26
> **Arndt said:**
> Rather than letting the program run until an exception occurs, I put a breakpoint at its start and single stepped. But my results are the same as Bachstelze's: eax becomes 0. How exactly do you determine what the result is?

Bachstelze first puts some value in the eax, and safekeeps the value into ebx before xoring it. This works fine for me. My  question now is why is it when I write the xor eax,eax directly without giving it any value or safekeeping it, I get 0xffffffff?

---

### Post by Arndt on 2011-12-26
> **das86 said:**
> Bachstelze first puts some value in the eax, and safekeeps the value into ebx before xoring it. This works fine for me. My  question now is why is it when I write the xor eax,eax directly without giving it any value or safekeeping it, I get 0xffffffff?

I said: when I do what you describe, I get 0; and my question was: how do you determine what is in eax at that point? Show us the entire operation: source, compilation, running.

---

### Post by worksofcruft on 2011-12-27
> **das86 said:**
> Bachstelze first puts some value in the eax, and safekeeps the value into ebx before xoring it. This works fine for me. My  question now is why is it when I write the xor eax,eax directly without giving it any value or safekeeping it, I get 0xffffffff?

 I suspect your simple program is 'user-level' code only. Whereas the debugger has access to 'system-level' code and therefore has access to hardware (such as the CPU's registers).

Linux is a 'protected' O.S. 
One of the things a protected O.S. does is not allow code at the user-level to directly access hardware. You would need to write or call system-level code of some sort for your program to get actual access to hardware. 

Of interest to you might be to create a 'list file' the next time you build your program. Then look at how 'eax' is resolved in the listing. I suspect it resolves to an address and NOT an internal CPU register. And that is why your program returns 0xffffffff: Your code is reading an address that is not any type of memory or register, i.e. the data bus has no data on it.  0xffffffff is what an empty data bus returns.

---

### Post by Arndt on 2011-12-28
> **worksofcruft said:**
> I suspect your simple program is 'user-level' code only. Whereas the debugger has access to 'system-level' code and therefore has access to hardware (such as the CPU's registers).


If anything, the program has more direct access to the registers than the debugger. The debugger needs to ask the kernel for what the values of the saved registers in another process are; the program uses them directly. But both are user-level programs.

---

### Post by ofnuts on 2011-12-29
> **worksofcruft said:**
> I suspect your simple program is 'user-level' code only. Whereas the debugger has access to 'system-level' code and therefore has access to hardware (such as the CPU's registers).

Linux is a 'protected' O.S. 
One of the things a protected O.S. does is not allow code at the user-level to directly access hardware. You would need to write or call system-level code of some sort for your program to get actual access to hardware. 

Of interest to you might be to create a 'list file' the next time you build your program. Then look at how 'eax' is resolved in the listing. I suspect it resolves to an address and NOT an internal CPU register. And that is why your program returns 0xffffffff: Your code is reading an address that is not any type of memory or register, i.e. the data bus has no data on it.  0xffffffff is what an empty data bus returns.
Hmmm. A debugger is supposed to  show us what it says, otherwise there is no point using it?

---

### Post by Arndt on 2012-01-02
It would be interested to know what the problem was. das86, did you resolve the issue?

---

