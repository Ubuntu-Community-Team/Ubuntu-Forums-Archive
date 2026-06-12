---
title: "GNU assembler problem: consistent segfaults."
date: 2007-03-08
forum: Programming Talk
---

### Post by Ian Maxwell on 2007-03-08
I'm attempting to learn assembly from [this guide]("http://programminggroundup.blogspot.com/2007/01/chapter-3-your-first-programs.html"), and entered the first program found on the linked page. I assembled and linked it with the following commands:
```
as -o exit.o exit.s
ld -o exit exit.o
```
This produced object and ELF files as expected.

On attempting to run the program, I got a segfault:
```
Segmentation fault (core dumped)
```

Since I don't yet know assembly, I didn't know if this was a problem with the code or some other problem, so I found some other source code examples elsewhere, all of which gave segfaults when assembled, linked, and run.

I have attached a gzipped copy of the ELF. My first question is whether it works properly on other people's machines (it's not supposed to do anything but return a number to the kernel). My second question is whether anyone can imagine what could cause this problem.

---

### Post by Wybiral on 2007-03-08
Can you post the actual assembly code used to assemble the program? I might be able to help if you do.

BTW, it's nice to see others around here interested in assembly, keep it up!)

---

### Post by Ian Maxwell on 2007-03-08
....dur dur dur. Never mind, it was a stupid error.

If you're curious, here was the code I had.

```

# PURPOSE:  Simple program that exits and returns a
#           status code to the kernel
#

# INPUT:    none
#

# OUTPUT:   Returns a status code. This can be viewed
#           by typing
#
#           echo $?
#
#           after running the program.

# VARIABLES:
#           %eax    holds the system call number
#           %ebx    holds the return status
#
.section .data

.section .text
.globl _start
_start:
movl $1, %eax   # This is the linux kernel command
                # number for exiting a program.

movl $2, %eax   # This is the status number we will
                # return to the operating system.

int $0x80       # This wakes up the kernel to run
                # the exit command.
```

That last %eax was, of course, supposed to be %ebx. This doesn't explain what was wrong with the other examples I found, but I'm happy for now as this one seems to work.

And thank you for the encouragement! I've been meaning to learn assembly for years now, mainly out of a hope it will grant me additional insight into How All This Stuff Really Works.

---

### Post by Wybiral on 2007-03-08
> **Ian Maxwell said:**
> ....dur dur dur. Never mind, it was a stupid error.

If you're curious, here was the code I had.

```

# PURPOSE:  Simple program that exits and returns a
#           status code to the kernel
#

# INPUT:    none
#

# OUTPUT:   Returns a status code. This can be viewed
#           by typing
#
#           echo $?
#
#           after running the program.

# VARIABLES:
#           %eax    holds the system call number
#           %ebx    holds the return status
#
.section .data

.section .text
.globl _start
_start:
movl $1, %eax   # This is the linux kernel command
                # number for exiting a program.

movl $2, %eax   # This is the status number we will
                # return to the operating system.

int $0x80       # This wakes up the kernel to run
                # the exit command.
```

That last %eax was, of course, supposed to be %ebx. This doesn't explain what was wrong with the other examples I found, but I'm happy for now as this one seems to work.

And thank you for the encouragement! I've been meaning to learn assembly for years now, mainly out of a hope it will grant me additional insight into How All This Stuff Really Works.

Try:

```

movl $1, %eax
movl $2, %ebx
int $0x80

```

Your are changing the value of "eax" two times... This is unnecessary, EBX is the return value.

Once again, hope this helps, good luck!

---

### Post by Wybiral on 2007-03-08
NM, seems you have solve the problem. Cool. Still email me if you have any problems with GAS assembly.

---

### Post by rplantz on 2007-03-09
Instead of a _start function that uses the int $0x80 instruction, you can use a main function and use the C libraries. The trick is to use gcc for linking, which automatically pulls in the C libraries. You can use ld, but then you have to list all the required C libraries. Doing it this way also allows you to use the C standard libraries for I/O. For example:
```

# helloWorld.s
# Hello world program using printf

        .data
theString:
        .string "Hello world.\n"

        .text
        .globl  main

main:
        pushl   %ebp        # save base pointer
        movl    %esp, %ebp  # set new base pointer

        pushl   $theString  # pass address to printf
        call	printf
        addl    $4, %esp    # remove argument from stack
        
        movl    $0, %eax    # return 0;
        movl    %ebp, %esp  # restore stack pointer
        popl    %ebp        # restore base pointer
        ret

```
Then assemble, link, and run the program:
```

bob@ubuntu:~/programing$ as -32 helloWorld.s -o helloWorld.o
bob@ubuntu:~/programing$ gcc -m32 helloWorld.o -o helloWorld
bob@ubuntu:~/programing$ ./helloWorld 
Hello world.
bob@ubuntu:~/programing$ 

```
The -32 and -m32 options are required if you're running an x86-64 system.

---

### Post by Wybiral on 2007-03-09
I agree that using gcc is a much easier way to assemble, but it does have a disadvantage...
The resulting executables are VERY large compared to simple handcoded assembly.
Also, you can use gcc as the assembler, "gcc helloWorld.s -o helloWorld" instead of using "as"
But yeah, with larger assembly projects, it is usually best to go ahead and use C libraries...
It's worth it.
You can also draft in C and then dump the assembly... Then optimize.

---

