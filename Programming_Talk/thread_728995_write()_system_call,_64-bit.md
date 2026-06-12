---
title: "write() system call, 64-bit"
date: 2008-03-19
forum: Programming Talk
---

### Post by rplantz on 2008-03-19
The default address size is 64 bits in 64-bit mode. But when I look at the assembly language for the write() syscall, they use only 32 bits of the address:
```

	.file	"oneChar.c"
	.data
	.type	aLetter, @object
	.size	aLetter, 1
aLetter:
	.byte	65
	.text
.globl main
	.type	main, @function
main:
	pushq	%rbp             // <== 64-bit addresses
	movq	%rsp, %rbp       // <==
	movl	$1, %edx
	movl	$aLetter, %esi   // <== 32-bit address
	movl	$1, %edi
	call	write
	movl	$0, %eax
	leave
	ret
	.size	main, .-main
	.ident	"GCC: (GNU) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)"
	.section	.note.GNU-stack,"",@progbits

```

Can anyone point me to discussions of what is going on here?

---

### Post by NathanB on 2008-03-19
First, let me state that you will only have a 'narrow' picture of what's going on if you only look at a compiler's "source" listing.  It's major use is to provide experienced coders with a quick verification that the compiler did *exactly* what you told it to do.  For learning purposes, you should look at how an object file is constructed, the duties and processes of how a linker constructs an executable file (and the format of such), and how the Operating System 'loader' arranges your binary into memory in preperation for execution.

Second, to help you visualize how modern computers work, pretend you've got a table, array, hash (or whatever term is comfortable for you) which looks like this:

index | value
------+----------------------
  0   | "segmentation fault"
  1   | "1800 Penn. Ave., US, Earth"
  2   | "10 Downing St., UK, Earth"
  3   | "42 Clarke Orbit, 1701-G, Jupiter"

You can already see that we can travel quite a distance with just small increments of the index.  Going from 1 to 2, we've crossed an ocean.  Going from 2 to 3, we've traded planets.

A 64-bit value can reference up to ~18 TeraBytes of individual address units.  However, the system does not allocate memory to us (our application's process) in individual byte-sized pieces -- we get it in page-sized chuncks.  If any process requires more than a 32-bit wide index value (and the associated 4-Gigabyte sized "look-up" table), then it is time to buy a straight-jacket for the coder of that process.  :)

Do some Google searches and visit your local library and bookstore.  Find instructional material on linkers, loaders, modern operating systems, paging, memory-management.

Nathan.

---

### Post by rplantz on 2008-03-19
Well, I've been reading the abi ([www.x86-64.org/documentation/abi.pdf](www.x86-64.org/documentation/abi.pdf)).

It says "The AMD64 architecture usually does not allow an instruction to encode arbitrary 64-bit constants as immediate operand." So I thought that the developers were keeping data within a 32-bit range so they could use immediate operands.

Yet I get
```

  11 0004 49BAEFCD 	        movq    $0x1234567890abcdef, %r10  # 64-bit immediate
  11      AB907856 
  11      3412
  12 000e 41BB7856 	        movl    $0x12345678, %r11d         # 32-bit immediate
  12      3412
  13 0014 6641BC34 	        movw    $0x1234, %r12w             # 16-bit immediate
  13      12
  14 0019 41B512   	        movb    $0x12, %r13b               # 8-bit immediate

```

The abi also states "By default only data larger than 65535 bytes will be placed in the large data section." I also see that calling printf uses a 32-bit address for passing the formatting string. So I guess that the developers place things like program text strings in a 32-bit address space.

It confused me because both the Intel and AMD manuals state that addresses are 64 bits by default.

Nathan, first let me thank you for your response. I hope you don't take this wrong, but I've got some 40 years of coding experience, mostly in assembly language. And I have a pretty good understanding of how several memory management systems work, starting from those in the early 1970s. So I realize that a 64-bit addressing space is not needed for most programs. But when the manual says that addresses are 64 bits, but the programmer explicitly codes it up as 32 bits, I would like to see the reason(s). After all. somebody, somewhere made that decision. Of course, I'm a bit compulsive. :)

Bob

---

### Post by NathanB on 2008-03-20
> **rplantz said:**
> 
Nathan, first let me thank you for your response. I hope you don't take this wrong, but I've got some 40 years of coding experience, mostly in assembly language. And I have a pretty good understanding of how several memory management systems work, starting from those in the early 1970s. So I realize that a 64-bit addressing space is not needed for most programs. But when the manual says that addresses are 64 bits, but the programmer explicitly codes it up as 32 bits, I would like to see the reason(s). After all. somebody, somewhere made that decision. Of course, I'm a bit compulsive. :)

Bob

Bob,

I can certainly understand the compulsion and the desire for answers.  We are "few and far between" as the saying goes.  :)

Have you tried contacting any of Linux devs? the people who actually wrote this code??  Some possible haunts:
[http://lists.gnu.org/](http://lists.gnu.org/)
[http://vger.kernel.org/](http://vger.kernel.org/)

This 64-bit stuff is a complete mystery to me.  It is still "cutting-edge" tech in the sense that only a small percentage of us have made the leap to that platform, the tools a sparse (NASM only recently made the leap, for instance), books, tutes, and examples are very rare, etc...  So, please, pretty please, after you blaze a trail through this jungle, don't forget to contribute back to the community so the rest of us can follow your foot-steps.

Happy conditional branching!

Nathan.

---

### Post by rplantz on 2008-03-20
> **NathanB said:**
> 
This 64-bit stuff is a complete mystery to me.  It is still "cutting-edge" tech in the sense that only a small percentage of us have made the leap to that platform, the tools a sparse (NASM only recently made the leap, for instance), books, tutes, and examples are very rare, etc...  So, please, pretty please, after you blaze a trail through this jungle, don't forget to contribute back to the community so the rest of us can follow your foot-steps.

Happy conditional branching!

Nathan.

This is exactly the reason I'm asking these questions -- so I can try to put things together in an easily accessible form.

Bob

---

### Post by rabatitat on 2008-07-14
I'm porting some of my practice programs to try and make them work on my AMD 3200+ system running the desktop version of Ubuntu 8.04.

I've hit a wall with the open system call. It returns an invalid address error. The program is supposed to get 2 arguments from the command line ("progname file1 file2").

My code for the open syscall in order to get the file descriptor for the first file looks like this:

movq  %rsp, %rbp
movq  $5, %rax
movq  16(%rbp), %rbx <--- supposed to return the address of the first argument...
movq  $0, %rcx
movq  $0666, %rdx
int   0x80

This returns the -14 error to %eax instead of the file descriptor for the file1 (argument)...

You guys are more experienced than I am with asm in general...

Where'd I go wrong?

I read the stack frame layout from the ABI provided by x86-64.org and I think I am following the offset values (8bytes) properly...

---

### Post by rplantz on 2008-07-14
> **rabatitat said:**
> 
I've hit a wall with the open system call. It returns an invalid address error. The program is supposed to get 2 arguments from the command line ("progname file1 file2").

My code for the open syscall in order to get the file descriptor for the first file looks like this:

movq  %rsp, %rbp
movq  $5, %rax
movq  16(%rbp), %rbx <--- supposed to return the address of the first argument...
movq  $0, %rcx
movq  $0666, %rdx
int   0x80

This returns the -14 error to %eax instead of the file descriptor for the file1 (argument)...

You guys are more experienced than I am with asm in general...

Where'd I go wrong?

I read the stack frame layout from the ABI provided by x86-64.org and I think I am following the offset values (8bytes) properly...

Two errors jump out at me.
First, I think that
```

movq  16(%rbp), %rbx <--- supposed to return the address of the first argument...

```
gets a pointer to the address of the first argument. I think you need to do:
```

movq  16(%rbp), %rbx
movq  (%rbx), %rbx

```

Second, you're missing a '$':
```

int $0x80

```

---

### Post by rabatitat on 2008-07-19
Thanks for the reply rplantz, although what I posted wasn't the exact code. Sorry for the missing $ on the interrupt. But the other ops are the problem. Running the same chip as you are AMD Athlon 64 3200+ on Ubuntu 8.04.

I figured it out after reviewing the ABI for the x86-64 supplied by AMD, the registers used for passing arguments has changed.

x86:
%rbx - 1st arg, %rcx - 2nd arg, %rdx - 3rd arg, ...

x86 - 64:

%rdi - 1st arg, %rsi - 2nd arg, %rdx - 3rd arg, ...

Also the system call numbers have changed for x86-64. Check the unistd_64.h file in your /usr/include/asm folder.

Open syscall number change

x86: 5

x86 - 64: 2

INT $0x80 has been changed to 'syscall' on the x86-64 environment.

So new code:

movq  $2,%rax  #syscall number loaded to %rax
movq  16(%rbp),%rdi  #1st arg would be the file name
movq  $0,%rsi  #2nd arg flags for opening file 0-readonly
movq  $0666,%rdx #3rd arg file permissions
syscall #replacement for int $0x80

Returns the file descriptor to %rax

Hope this helps the other asm programmers out there making the shift to 64-bit.

---

### Post by rplantz on 2008-07-19
> **rabatitat said:**
> 
I figured it out after reviewing the ABI for the x86-64 supplied by AMD, the registers used for passing arguments has changed.

x86:
%rbx - 1st arg, %rcx - 2nd arg, %rdx - 3rd arg, ...

x86 - 64:
%rdi - 1st arg, %rsi - 2nd arg, %rdx - 3rd arg, ...

Yeah, I knew that they had changed. Passing in registers (up to 6 arguments) is also used for calling C/C++ functions. And the arguments are read left-to-right. Recall that in 32-bit code the arguments are all pushed onto the stack in right-to-left order.

> 
INT $0x80 has been changed to 'syscall' on the x86-64 environment.

So new code:

movq  $2,%rax  #syscall number loaded to %rax
movq  16(%rbp),%rdi  #1st arg would be the file name
movq  $0,%rsi  #2nd arg flags for opening file 0-readonly
movq  $0666,%rdx #3rd arg file permissions
syscall #replacement for int $0x80

I think that int $0x80 still works, but the recommendation is syscall. syscall doesn't go through the interrupt descriptor table (IDT). It save RIP in RCX, then loads RIP from the LSTAR register. So it has a lower latency. I don't recall if the same argument passing registers work for int $0x80.

By the way, if you are willing to link with the C libraries, you can do
```

movq  16(%rbp),%rdi  #1st arg would be the file name
movq  $0,%rsi  #2nd arg flags for opening file 0-readonly
movq  $0666,%rdx #3rd arg file permissions
call  open

```
Name your main function "main" and use gcc for the linking phase.

You can also use the C standard library functions this way to do formatted I/O. Besides the regular arguments, you have to pass the number of floating point arguments in eax. For example, if x is an int and y a double:
```

printf("x = %i and y = %lf\n", x, y);

```
can be done in assembly language:
```

        .section  .rodata
format: .string "x = %i and y = %lf\n"
        .text
     ----------
        movl    $1, %eax
        movl    $format, %edi
        movl    x(%rbp), %esi
        movq    y(%rbp), %rdx
        call    printf

```
This assumes that x and y are local variables on the stack. Note that things in the .rodata section have 32-bit addresses. If you have a string in the stack frame, you need to use 64-bit operands.

I used to teach assembly language. I used the C calls in my class. Most textbooks have their own libraries, etc. I wanted my students to see how assembly language interfaces with C/C++ because that's where they are most apt to use it.

---

### Post by rabatitat on 2008-07-19
Thanks again. :)

Yup, I do use inline asm in some programs. asm is THE way to really learn how the PC works and to make it work right. 

I'm mainly studying asm for x86-64 to get used to the new environment and as always for the fun of it.

int $0x80 still works with 32-bit mode. Most 32 bit asm code will still run unchanged. It won't work with the new method of passing registers.

---

### Post by rplantz on 2008-07-19
> **rabatitat said:**
> Thanks again. :)


And thank you for your contributions.

I told my students that you should avoid writing in assembly language unless (1) the compiler hasn't done a good enough job, or (2) C won't let you do it. But the only way to know if either of these applies is to be able to read the assembly language the compiler produces.

I also told them what you said -- it's the only way to really understand how the machine works.

And, I'm with you. It's simply fun. I'm retired, and I still enjoy programming in assembly language. :)

---

### Post by monkeyking on 2009-12-23
Hi
did you ever figure this 32bit on a 64bit platform?

I'm having similar problems, just with the read() function.

---

