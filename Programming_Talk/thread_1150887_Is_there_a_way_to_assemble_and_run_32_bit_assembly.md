---
title: "Is there a way to assemble and run 32 bit assembly code in amd64 environment?"
date: 2009-05-06
forum: Programming Talk
---

### Post by barisurum on 2009-05-06
The title says it all. So I want to learn assambly as a hobby but 32 bit code doesn't assemble in my amd64 machine and 64 bit YASM. I cannot find any good amd64 assembly tutorials online.

---

### Post by NathanB on 2009-05-06
Here are a couple of resources you may have missed:

[http://www.vikaskumar.org/wiki/index.php?title=X86-64_Tutorial](http://www.vikaskumar.org/wiki/index.php?title=X86-64_Tutorial)

[http://www.x86-64.org/about.html](http://www.x86-64.org/about.html)

If that isn't enough material, then install VirtualBox...

[http://www.virtualbox.org/](http://www.virtualbox.org/)

...and boot a 32-bit OS to learn ASM on.

---

### Post by barisurum on 2009-05-07
Ok I will install ubuntu 32 bit in a 5 gb virtual harddisk thanks...

---

### Post by samjh on 2009-05-07
What sort of problems are you having?

Most of the 32-bit stuff should work.  Just make sure to use the correct names and such.  For example, in amd64 you need to use rsp and rbp instead of esp and ebp (the stack pointer and base pointer in x86), and use the corresponding 64-bit instructions popq and pushq.

If in doubt, write little test programs in C, and compile using the -S switch to generate assembly code.  You'll need to be familiar with gas' AT&T syntax to read the generated code.

[EDIT]

If you want, you can use the -f option in yasm to specify elf32 as the output file, and then link it using -b and -m options.

Example:
```
yasm -f elf32 my32bitprogram.asm
ld -b elf32-i386 -m elf_i386 -o my32bitprogram my32bitprogram.o
```
That will let you write and run 32-bit assembly on a 64-bit machine. :)

---

### Post by barisurum on 2009-05-07
WOW Thanks alot sam! I don't know how, but it works! Here is the code I tried with:

```

section .data
	fakewarn:     db 'CPU temperature too high! CPU will surely fry!',10  
	fakewarnL:  equ $-fakewarn             
	                                   

section .text
	global _start

_start:
	mov eax,4            
	mov ebx,1            
	mov ecx,fakewarn        
	mov edx,fakewarnL     

	int 80h              

	mov eax,1            
	mov ebx,0            
	int 80h

```

As you can see it uses 32 bit registers and even uses "int 80h" to call the kernel instead of syscall.. Does it tell YASM to change the code?

edit: I recently found an excellent book to learn C++ by H. M. Deitel and P. J. Deitel. So I started learning C & CPP. I hope to learn enough to program plugins using csound. But I will keep in mind that I can use this again later. Thanks again.

---

### Post by samjh on 2009-05-07
The 32-bit registers aren't a big deal.  AMD64 architecture didn't abandon 32-bit registers, so the vast majority of them still work as long as you use the correct instructions and values. :)

What my instructions in the previous post does is tell YASM to generate 32-bit object code instead of 64-bit object code.  The linker then generates a 32-bit executable (-b switch) via its emulation feature (-m switch).

GAS, NASM, and YASM all support generation of object code for various architectures.  The GNU linker (ld) also has similar support.

---

### Post by Cracauer on 2009-05-08
> **barisurum said:**
> Ok I will install ubuntu 32 bit in a 5 gb virtual harddisk thanks...

No, do this:
gcc -v -m32 foo.c

It'll show you how to invoke the assemble on the base system in 32 bit mode (presumably also with -m32 but this will show you).

---

