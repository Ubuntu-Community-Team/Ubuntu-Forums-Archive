---
title: "problem with assembly..."
date: 2006-02-11
forum: Programming Talk
---

### Post by orlox on 2006-02-11
Well, I've been trying to get some decent knowledge of assembly language, but lately, all the executables I produce do not have execution permission. I tried to modify that as root but got nowhere...I believe the problem is with the linker, since I get the same error using either nasm or as...

to be more detailed, this is my incredibly basic program (it makes nothing but exit) wich used to work with no problems:
###############################################
 .section .data
 .section .text
 .globl _start
_start:
 movl $1, %eax  # this is the linux kernel command
                # number (system call) for exiting
                # a program
 movl $0, %ebx  # this is the status number we will
                # return to the operating system.
                # Change this around and it will
                # return different things to
                # echo $?
 int $0x80      # this wakes up the kernel to run
                # the exit command
###############################################
I save it as a.s and then I assemble it with 

"as a.s -o a.o"

and link it with

"ld a.o -o a"

wich generates an executable with no execution permissions (not even for root), so when go an do "./a" I get this message:

bash: ./a: Permission denied:

:confused: 

I have no idea of what made this fail, considering it used to work...
Any help would be truly appreciated [-o<

---

### Post by LordHunter317 on 2006-02-11
Grant execute with chmod +x.

---

### Post by orlox on 2006-02-11
nope, that didn't work either...I used:

"sudo chmod +x a"

where "a" is my executable, but the permissions remained the same, and i still get that permission denied message even when i try to run it as root...

---

