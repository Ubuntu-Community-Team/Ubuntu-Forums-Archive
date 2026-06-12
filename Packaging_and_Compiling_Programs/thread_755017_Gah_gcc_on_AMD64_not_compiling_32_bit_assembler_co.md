---
title: "Gah gcc on AMD64 not compiling 32 bit assembler code"
date: 2008-04-14
forum: Packaging and Compiling Programs
---

### Post by P_Hansson on 2008-04-14
Hi everyone!

(Edit: Please move to right forum if this is wrong.)

This is my first post here, I'm very new to Ubuntu and Linux. :)

At CS/university Linux is used is near every course, so I figured now would be a nice time to install it at home on my AMD64/I64 system.

Right now I have a project in the initial compiler technology course, which requires me to output to Intel x86 assembly code. Currently we're in design stage so we'd like to verify our design. But for some reason I can't compile the 32 bit code with gcc to link with C library (which works fine at university), because it complains about the push and pop instructions. Presumably it's because I'm not forcing it to compile for x86 targets - how do I do that?

I'm reading GCC manual but I'm not getting it to work.

An example of errors for anyone interested with most simple command:
```
petter@PETTERH2:~/eda180/project/design$ gcc errors.s


errors.s: Assembler messages:
errors.s:9: Error: suffix or operands invalid for `push'
errors.s:11: Error: suffix or operands invalid for `push'
errors.s:15: Error: suffix or operands invalid for `pop'
errors.s:17: Error: suffix or operands invalid for `pop'
errors.s:18: Error: suffix or operands invalid for `push'
```

Related file:
```
#errors.s

	.data
disp:	.skip	4		#(max number of used nested levels - 1) * 4 bytes

	.text
	.global	main
main:
	pushl	%ebp		#C lib expects EBP to be unchanged
	subl	$4, %esp	#allocate local variables (Integer x)
	pushl	disp+0		#save old display (kind of redundant here but...)
	movl	%esp, disp+0	#set current display level to start at end of local vars
	movl	$1, 0(%esp)	#x = 1
	#call	main_p1
	popl	disp+0		#restore display
	addl	$4, %esp	#remove local variables
	popl	%ebp		#restore EBP
	pushl	$0		#signify normal termination from main
	call	exit
```

---

### Post by P_Hansson on 2008-04-14
Solved myself.

Turns out I didn't have 32 bit libraries installed.

---

