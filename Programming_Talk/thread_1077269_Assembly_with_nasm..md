---
title: "Assembly with nasm."
date: 2009-02-22
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-02-22
I have just begun assembly and i am a noob.

Can someone check this simple program to add 2 numbers from memory. I am getting a error when linking and i dont know what it means.

section .data
	x: db 13d
	y: db 15d
	CPU 8086
section .text
	global _start

_start:
	mov bx, x
	mov bl, [x]
	add bl, [y]
	
	int 80h
	mov ax,1
	mov bx,0
	int 80h

The error i get after ld is
first.o: In function `_start':
first.asm:(.text+0x2): relocation truncated to fit: R_386_16 against `.data'

Why is this?

---

### Post by Zugzwang on 2009-02-22
What are your "ld" options? Actually, I wonder if "ld" can actually be used to link 16-bit programs.

---

### Post by 7raTEYdCql on 2009-02-22
I simply used ld -o name.name.o

---

### Post by 7raTEYdCql on 2009-02-22
How do you change ld to make it work for a 16 bit instruction set??

---

### Post by Zugzwang on 2009-02-22
> **i.mehrzad said:**
> I simply used ld -o name.name.o

Can't be - "name.name.o" will be the name of the output file this way.

> **i.mehrzad said:**
> 
How do you change ld to make it work for a 16 bit instruction set?? 


ld will only build executables for modern operating systems, running in protected mode, defaulting to 32 bit instructions. So you will need to add "BITS 32" to your NASM program. This does not mean that you cannot use the 16-bit instructions, but you are forced to have your program running in protected mode, which did not exist for the 8086. Might work anyway, but memory addressing is different here.

There has also been a project for a 16-bit "ld" linker, use google for finding that. Don't know if that works.

---

### Post by 7raTEYdCql on 2009-02-22
Problem is that in college they are teaching masm, in native 8086 form. 
I dont want to get confused, i am anyway adapting to the variations in syntax. 
In order to simlify things i am using CPU 8086. 

Anyway, is nemiver a good replacement for codeview??

---

### Post by Frank Kotler on 2009-02-22
You don't want "cpu 8086" in conjunction with "int 80h"!

If you want to run dos code - which is apparently what they're teaching in college - look into "dosemu". It should allow you to run 8086 code.

What you want for a Linux program is:

; nasm -f elf mygem.asm
; ld -o mygem mygem.o

global _start ; tell ld about it

section .text
_start:

mov eax, 1 ; __NR_exit
mov bl, 42
int 80h

All that does is exit, but if you then type "echo $?", it'll print the "exit code"... which we said was 42.

You can add code to add two numbers (your code is okay) and display the answer with "echo $?" - only good up to 255. If you want to print the answer... well, we print characters, not numbers. If you print the number 42, you'll see 'B', not '4' followed by '2', which is what you want. (true of dos, too, BTW) We print something like:

mov edx, buffer length
mov ecx, address of buffer
mov ebx, 1 (stdout - the screen)
mov eax, 4 ;__NR_write
int 80h

Note that ecx is the address of the text to print, not the number to print! (if you need help with this, there are lots of examples, ask...)

If you need to practice with "college code" - dosemu - int 80h is not a drop-in replacement for int 21h - it just won't work!

Best,
Frank

---

