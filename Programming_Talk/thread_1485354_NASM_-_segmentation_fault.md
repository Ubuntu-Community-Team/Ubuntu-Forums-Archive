---
title: "NASM - segmentation fault"
date: 2010-05-16
forum: Programming Talk
---

### Post by luciantw on 2010-05-16
Hey guys, my class is taught in MASM but I'm trying to do it with NASM. I'm pretty close, I get the correct result in EAX(10000h) when DumpRegs is called, but it still displays that there is a segmentation fault. How do I correct this?

```
; Purpose: Subtract three integers 

%INCLUDE "Along32.inc"

segment .code
	global 	_start
_start:

	mov	eax, 50000h	;First integer
	sub	eax, 20000h
	sub	eax, 20000h
	call	DumpRegs		;Display registers on screen

        leave                     
        ret
```

---

### Post by schauerlich on 2010-05-16
1) Why is that return there? it pops something off the stack and sticks it in the PC, which may cause a segfault if the top of the stack is junk
2) you never exit, so it'll keep fetching instructions past the end of your program until it gets to something that's junk and causes a segfault
3) related to 2, how are you running this? stepping through with gdb/some debugger? 
4) are you linking it after you assemble? 
etc

---

### Post by snova on 2010-05-16
> **luciantw said:**
> Hey guys, my class is taught in MASM but I'm trying to do it with NASM. I'm pretty close, I get the correct result in EAX(10000h) when DumpRegs is called, but it still displays that there is a segmentation fault. How do I correct this?

```
; Purpose: Subtract three integers 

%INCLUDE "Along32.inc"

segment .code
	global 	_start
_start:

	mov	eax, 50000h	;First integer
	sub	eax, 20000h
	sub	eax, 20000h
	call	DumpRegs		;Display registers on screen

        leave                     
        ret
```

What exactly is segfaulting? If DumpRegs is being called properly and _start is what I think it is, leave/ret won't work because this "function" isn't supposed to return.

To directly solve your problem, you could call exit() instead, but I question why you're writing _start in the first place instead of main().

---

### Post by luciantw on 2010-05-16
This is my first day programming in assembly.

1)I saw it in some example code and put it in thinking it might be how to exit. I've now taken it out.

2)I am embarrassed to admit this, I do not know how to exit. Will you please tell me how?

3)I wrote the code in gedit I use the Along32 library which is modeled after the Irvine32 library which is from the text book used in my class. I wrote the code, made a .o file and a .bin file and executed the .bin with ./file.bin in terminal

4)Yes, I think I am doing so with this command
ld -lAlong32 --dynamic-linker /lib/ld-linux.so.2 -o lab0.bin lab0.o

---

### Post by luciantw on 2010-05-16
here is what dump regs displays in terminal

```
  EAX=00010000  EBX=00862FF4  ECX=008607F3  EDX=008550C0
  ESI=BFCC795C  EDI=08048548  EBP=00000000  ESP=BFCC7950
  EIP=0804855C  EFL=00200246  CF=0  SF=0  ZF=1  OF=0  AF=0  PF=1

Segmentation fault

```

---

### Post by schauerlich on 2010-05-16
I'm assuming you have some familiarity with C. in C, you start with main(), and at the end, you return 0. The problem with your code is, you're treating _start like it's a subroutine (like main) when it's not. There's nothing to leave/ret from, ret segfaults because it just pops whatever is on the stack and tries to access it. Since it's highly unlikely that random junk is going to point to somewhere within your program, it segfaults.

If you want to do it in a "C-like" way, replace "_start" with "main" and link with libc.

Also, you should try putting a dummy instruction at the end (like "movl %eax, %eax") and then set a breakpoint there in gdb. then you can hit run and see the results, without having to call DumpRegs or worry about going off the end of your program.

---

### Post by schauerlich on 2010-05-16
Also: my professor has a [free textbook](http://heather.cs.ucdavis.edu/~matloff/50/PLN/CompSystsBookS2010.pdf) available online that I've found very helpful. If you get confused in your class, take a look over there and see if the way he explains it is any clearer. Ch. 6 is on subroutines.

---

### Post by luciantw on 2010-05-16
I am only very loosely familiar with C, this is not an assembly class per se, it is a PC architecture class with a splash of assembly thrown in.  When i change _start to main and run the command
ld -lAlong32 --dynamic-linker /lib/ld-linux.so.2 -o lab0.bin lab0.o

I get the following error
ld: warning: cannot find entry symbol _start; not setting start address

I'm still a tad confused about how to exit, do I have to call another library or is there another way?

---

### Post by lisati on 2010-05-16
Seeing "Leave" in an ASM source file has stirred a recollection of having seen it being used in conjunction with an "Enter" statement in a subroutine for an 80286 machine. [citation needed]

In other words, I'm wondering if there's a better way of doing the run-in and end-of-program tidy-up & exit for a stand-alone program.

---

### Post by schauerlich on 2010-05-16
> **luciantw said:**
> I get the following error
ld: warning: cannot find entry symbol _start; not setting start address


When a program runs, its point of entry is _start. If you're doing a standalone program, often times you don't have to bother linking to the C library and can just use _start like you did in your OP. However, if you do that, you do NOT want to use leave and ret, as those instructions are used only in subroutines.

To link to the C library, add "-lc" to the ld command.

---

### Post by luciantw on 2010-05-16
@ schauerlich, you go to UC Davis? I almost went there myself. 

You guys have all been massively helpful, thank you. Does this forum have a "thanks" option? 

Here is my new code, which no longer causes a seg fault. I don't know what the last three lines of code are doing, or even if this is bad form as I found them poking around them internet. What do the last three lines do, and are they acceptable to use? I am not  a comp sci major, so please excuse my ignorance.

```
%INCLUDE "Along32.inc"

segment .code
	global _start
_start:

	mov	eax, 50000h		;First integer
	sub	eax, 20000h
	sub	eax, 20000h
	call	DumpRegs		;Display registers on screen

                      
	mov	eax,1			;End program
	mov	ebx,0		
	int	80h	
```

---

### Post by snova on 2010-05-16
> **luciantw said:**
> You guys have all been massively helpful, thank you. Does this forum have a "thanks" option?

It used to; not anymore.

> Here is my new code, which no longer causes a seg fault. I don't know what the last three lines of code are doing, or even if this is bad form as I found them poking around them internet. What do the last three lines do, and are they acceptable to use? I am not  a comp sci major, so please excuse my ignorance.

```
%INCLUDE "Along32.inc"

segment .code
	global _start
_start:

	mov	eax, 50000h		;First integer
	sub	eax, 20000h
	sub	eax, 20000h
	call	DumpRegs		;Display registers on screen

                      
	mov	eax,1			;End program
	mov	ebx,0		
	int	80h	
```

It is acceptable so long as you do not mind being tied to Linux syscalls. "int 80h" issues a software interrupt, which is a simple means of performing a kernel syscall. eax contains the particular call to make (1 is exit()) and ebx contains the exit code.

---

### Post by luciantw on 2010-05-16
Without importing the C libraries I can't use exit()?

---

### Post by schauerlich on 2010-05-16
> **luciantw said:**
> Without importing the C libraries I can't use exit()?

exit is a system call, which you can use without libc. you did so in your post above (with int 80h)

---

### Post by snova on 2010-05-16
> **luciantw said:**
> Without importing the C libraries I can't use exit()?

Which exit() are we talking about?

There is a syscall called exit() (C's version is _exit()) which you are calling, and libc's exit() which eventually does the same thing- issues a syscall to directly end the program. libc also performs a few cleanup actions, however.

---

### Post by luciantw on 2010-05-16
I was referencing the syscall which I see I was calling. I'm satisfied with my first attempt at assembly, thank you all for your help!

---

### Post by lisati on 2010-05-16
> **luciantw said:**
> I was referencing the syscall which I see I was calling. I'm satisfied with my first attempt at assembly, thank you all for your help!

It's good that you made progress with your code. Enjoy your adventure.

Side note: My experience of coding x86 assembly is largely confined to 16-bit MS-DOS programs - off the top of my head, I can think of two system calls for exiting a program in that environment, and a third approach that *sometimes* works.

---

