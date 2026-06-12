---
title: "Linux Assembly linking problem (intel)"
date: 2011-04-02
forum: Programming Talk
---

### Post by tarek89 on 2011-04-02
Dear all

I am sorry for my newbie question but i just switched from dos assembling to Linux assembly

i just started the first program routine "hello world"
i used nasm 

the code is :

section .data
	hello:     db 'Hello world!',$  ; 'Hello world!' plus a linefeed character
	helloLen:  equ $-hello             ; Length of the 'Hello world!' string
	                                   ; (I'll explain soon)

section .text
	
	global _start

_start:
	mov eax,4            ; The system call for write (sys_write)
	mov ebx,1            ; File descriptor 1 - standard output
	lea ecx,hello       ; Put the offset of hello in ecx
	mov edx,helloLen     ; helloLen is a constant, so we don't need to say
	                     ;  mov edx,[helloLen] to get it's actual value
	int 80h              ; Call the kernel

	mov eax,1            ; The system call for exit (sys_exit)
	mov ebx,0            ; Exit with return code of 0 (no error)
	int 80h


--------

nothing simpler than that, i just assembled it with no errors

nasm -f elf hwl.asm 

it results no errors and the .o file was out

when linking 


ld -m elf_i386 -s -o hwl hwl.o

it gets me an error ,

hwl.o: In function `_start':
hwl.asm:(.text+0xa): relocation truncated to fit: R_386_16 against `.data'


i kept searching 2 days for this error all i got is that my OS and Arch are 64 and am writing a 32 program so i need 32 libraries to be able relocate my prog
but i still cant solve this problem
so if anybody can help me in it i would be so grateful , i dont want to go for dos lazy assembly

thanks all in advance, and sorry for interruption

---

### Post by NathanB on 2011-04-02
Replace "_start" with "main" and then use 'gcc' to link.

---

### Post by tarek89 on 2011-04-03
> **NathanB said:**
> Replace "_start" with "main" and then use 'gcc' to link.


Thank you for your reply
i made this change before and doesnt work 

today when i woke up all i did is to retry to link it and guess what it worked!!!

i dunno how but it worked, i think it cuz of busy memory or something i dont know

thank you admin you can close the topic

---

