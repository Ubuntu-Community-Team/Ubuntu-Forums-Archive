---
title: "Programming From the Ground Up (asm) file creation problem."
date: 2009-02-20
forum: Programming Talk
---

### Post by Mr.Fluke on 2009-02-20
So I read the 'Before you post' thread and searched online and in the forums for a solution without finding, or at least understanding a solution. Here's my problem:

I'm reading Programming From the Ground Up and doing the exercises it presents. At the end of the 5th chapter one of the exercises is to create a small program that creates a text file and writes a string into it. I'm having some trouble doing it, but I'm not sure what I'm doing wrong.

My understanding of assembly is limited to the first 60 pages or so of the earlier mentioned book. So when I've searched around for solutions online I've been drowning in either concepts I haven't seen yet or new syntaxes.

This is what I wrote:
```
.section .data
 file_name:
 .ascii "hello.txt\0"
 file_contents:
 .ascii "howdy!\0"

.section .text

# Variables
 .equ CALL_LINUX, 0x80

 .equ OPEN_INSTRUCTION, 5
 .equ CLOSE_INSTRUCTION, 6

 .equ OPEN_READONLY, 0
 .equ OPEN_CREATE_WRITEONLY, 03101
 .equ PERMISSIONS, 0666

 .equ READ_INSTRUCTION, 3
 .equ WRITE_INSTRUCTION, 4

 .equ EXIT_INSTRUCTION, 1

 .equ BUFFER_SIZE, 20
#

.globl _start
_start:

open_file:
 movl $OPEN_INSTRUCTION, %eax
 movl file_name, %ebx
 movl $OPEN_CREATE_WRITEONLY, %ecx
 movl $PERMISSIONS, %edx
 int $CALL_LINUX
 movl %eax, %ebx

write_into_file:
 movl $WRITE_INSTRUCTION, %eax
 # file descriptor should already be in ebx.
 movl file_contents, %ecx
 movl $BUFFER_SIZE, %edx

close_file:
 movl $CLOSE_INSTRUCTION, %eax
 # file descriptor should already be in ebx.
 int $CALL_LINUX

exit:
 movl $EXIT_INSTRUCTION, %eax
 # file descriptor should already be in ebx.
 int $CALL_LINUX

```

It assembles and links without error, and returns an exit code that (I think) is the file descriptor, but I never get a new file out of it. I'd sprinkle prints or something on it to find the problem if I knew how :P

If anyone could help me out with this I'd be very appreciative.

---

### Post by Frank Kotler on 2009-02-21
I'm Nasmist, but I think you'd want a "$" on "file_name" and "file_contents". I think without it, you get contents of memory, not the address (offset, Masm would call it), which is what those sys_calls want.

Best,
Frank

---

### Post by stroyan on 2009-02-21
The result is much better with the '$' characters that Frank suggested.
(It is still missing the call for write and trying to write more characters than your actual string.)
You can use the strace command (from the strace package) to show all system calls made by a program.
That can be very informative.  For your original program it shows the bad parameter and error result of the open call.
```

$ strace ./hello 
execve("./hello", ["./hello"], [/* 36 vars */]) = 0
open(umovestr: Input/output error
0x6c6c6568, O_WRONLY|O_CREAT|O_TRUNC|O_APPEND, 0666) = -1 EFAULT (Bad address)
close(-14)                              = -1 EBADF (Bad file descriptor)
_exit(-14)                              = ?

```

---

### Post by Mr.Fluke on 2009-02-21
Ooh, thank you. The new '$'s on the symbols yield me my hello.txt, very cool. I'm sure that strace tool will be helpful as well. Thanks so much guys, I'll take a couple more whacks at it and reread those sections on symbols and addressing.

---

### Post by Mr.Fluke on 2009-02-21
Woo! Fixed on my first whack. That strace tool is going to be enormously helpful I think. Here's the working version, with a fixed buffersize, added call to the kernel and the missing $s.

```
.section .data
	file_name:
	.ascii "hello.txt\0"
	file_contents:
	.ascii "howdy!\0"

.section .text

# Variables
	.equ CALL_LINUX, 0x80

	.equ OPEN_INSTRUCTION, 5
	.equ CLOSE_INSTRUCTION, 6

	.equ OPEN_READONLY, 0
	.equ OPEN_CREATE_WRITEONLY, 03101
	.equ PERMISSIONS, 0666

	.equ READ_INSTRUCTION, 3
	.equ WRITE_INSTRUCTION, 4

	.equ EXIT_INSTRUCTION, 1

	.equ BUFFER_SIZE, 7
#

.globl _start
_start:

open_file:
	movl $OPEN_INSTRUCTION, %eax
	movl $file_name, %ebx
	movl $OPEN_CREATE_WRITEONLY, %ecx
	movl $PERMISSIONS, %edx
	int $CALL_LINUX
	movl %eax, %ebx

write_into_file:
	movl $WRITE_INSTRUCTION, %eax
	# file descriptor should already be in ebx.
	movl $file_contents, %ecx
	movl $BUFFER_SIZE, %edx
	int $CALL_LINUX

close_file:
	movl $CLOSE_INSTRUCTION, %eax
	# file descriptor should already be in ebx.
	int $CALL_LINUX

exit:
	movl $EXIT_INSTRUCTION, %eax
	# file descriptor should already be in ebx.
	int $CALL_LINUX

```

Again thanks so much.

---

