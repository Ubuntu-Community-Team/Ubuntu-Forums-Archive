---
title: "simple asm code wont compile"
date: 2006-04-06
forum: Programming Talk
---

### Post by notquitehere188 on 2006-04-06
i have this simple asm code copied out of a tutorial book but it wont compile
it says that the mov lines are invalid assembler commands

```


#VARIABLES:
#		%eax holds the system call number
#		%ebx holds the return status
#
.section .data
.globl _start
_start:
mov1 $1, %eax		# this is a linux kernel command
			# number (system call) for exiting
			# a program

mov1 $0, %ebx		# this is the status number we will
			# return to the operating system.
			# Change this around and it will
			# return different things to
			# echo $?

int $0x80		# this wakes up the kernel to run
			# the exit command
```

---

### Post by cylon359 on 2006-04-06
What assembler are you using?  That code is AT&T syntax, so if you use nasm, it must be rewritten in Intel syntax...

---

### Post by Azrael on 2006-04-06
A *1* is not an *l*. Replace instances of *mov1* with *movl.* Also, your instructions are in the wrong section. Replace *.data* with *.text*.

(Compile with *as nameofyourprogram.s -o nameofyourprogram.o* and link with *ld nameofyourprogram.o -o nameofyourprogram.)*

---

### Post by notquitehere188 on 2006-04-06
thanks, guess i misread it, so far i am just following what the book says

---

### Post by vijayanand_sodadasi on 2006-04-07
[QUOTE=notquitehere188]thanks, guess i misread it, so far i am just following what the book says[/QUOTE]

I am copying the program text here:
Probably its the same tutorial book you are using:

```
#VARIABLES:
# %eax holds the system call number
# %ebx holds the return status
#
.section .data
.section .text
.globl _start
_start:
movl $1, %eax # this is the linux kernel command
# number (system call) for exiting
# a program
movl $0, %ebx # this is the status number we will
# return to the operating system.
# Change this around and it will
# return different things to
# echo $?
int $0x80 # this wakes up the kernel to run
# the exit command
```

However,  in the book it is mentioned that .data directive is optional for this program.

---

