---
title: "Language Converter?"
date: 2012-08-03
forum: Programming Talk
---

### Post by safiajen0055 on 2012-08-03
Hello Guys,

I would like to ask that Can we Convert assembly language into Machine language if yes then what is the device is useful for it?

---

### Post by Bachstelze on 2012-08-03
Well, yes. That's what assembly language is for, no? You use an assembler. Depending on what kind of assembly language you have, you can use GNU as (generally via gcc), or nasm/yasm.

---

### Post by Barrucadu on 2012-08-03
In the case of assembly, an assembler is used. In the general case, compilation is the process of taking one formal language (such as assembly, C, Haskell, whatever) and performing a semantics-preserving transformation into another formal language (such as machine code).

[http://en.wikipedia.org/wiki/Compiler](http://en.wikipedia.org/wiki/Compiler)

---

### Post by ofnuts on 2012-08-03
Let's add, just in case some people didn't figure that out by themselves, that one assembly language is more or less a one-on-one mapping of language instructions to machine instructions, so different architectures will have different assembly languages.

---

### Post by snip3r8 on 2012-08-03
Converting a language to machine code is the entire point of a compiler.

---

### Post by trent.josephsen on 2012-08-03
> **snip3r8 said:**
> Converting a language to machine code is the entire point of a compiler.
Not if the language is assembly. Then, it's an assembler.

Technically, the more "traditional" role of a compiler is translating a HLL into assembly, which it would then pass off to an assembler. But nowadays there often isn't a meaningful distinction to be made.

---

### Post by thek3nger on 2012-08-03
> **trent.josephsen said:**
> Not if the language is assembly. Then, it's an assembler.

Technically, the more "traditional" role of a compiler is translating a HLL into assembly, which it would then pass off to an assembler. But nowadays there often isn't a meaningful distinction to be made.

Well, these are the same steps performed by "compiler" like gcc. For example you can see the assembly step with the -S parameter and compile the assembly code with the "as" command. :)

---

### Post by trent.josephsen on 2012-08-03
True, but not all languages have an intermediate "assembly" step. Such as Java/Python/Perl, which are bytecode-compiled and interpreted on the fly. But I don't want to drag this further off topic, unless this is the kind of content OP wanted to hear...

---

### Post by thek3nger on 2012-08-03
Ah yes. Obviously. :) In my post I meant binary-compiled languages and not interpreted ones. :P

Ok... now we can stop with the OT.

---

### Post by xb12x on 2012-08-04
> **safiajen0055 said:**
> Hello Guys,

I would like to ask that Can we Convert assembly language into Machine language if yes then what is the device is useful for it?


If you want to see the actual machine language created by the assembler you can run objdump on the executable. 

Here is an example program written in GNU assembly, hello_asm.s

First build the program by assembling and linking. Then run objdump on the executable to create the list file. The list file will show the machine code for each assembly instruction. 

Build Instructions:
as -o hello_asm.o hello_asm.s
ld -o hello_asm -O0 hello_asm.o

Create list file showing machine code:
objdump -S hello_asm > hello_asm.lst

Here is the source file hello_asm.s
```

	## hello_asm.s

	## This is a basic demonstration of the GNU assembler, `as'.
	
	## Displays a string on the screen using write() system call

	## Build Instructions:
	## as -o hello_asm.o hello_asm.s
	## ld -o hello_asm -O0 hello_asm.o
        
        ## Create list file:
        ## objdump -S hello_asm > hello_asm.lst
        
########################################################################
	.section .data
hello:	
	.ascii 	"Hello, world!\n"
hello_len:
	.long 	. - hello
########################################################################
	.section .text
	.globl _start
	
_start:
	## display string using write () system call
	xorl %ebx, %ebx		# %ebx = 0
	movl $4, %eax		# write () system call
	xorl %ebx, %ebx		# %ebx = 0
	incl %ebx		# %ebx = 1, fd = stdout
	leal hello, %ecx	# %ecx ---> hello
	movl hello_len, %edx	# %edx = count
	int $0x80		# execute write () system call
	
	## terminate program via _exit () system call 
	xorl %eax, %eax		# %eax = 0
	incl %eax		# %eax = 1 system call _exit ()
	xorl %ebx, %ebx		# %ebx = 0 normal program return code
	int $0x80		# execute system call _exit ()

```


Here is the list file created by objdump, hello_asm.lst:
```

hello_asm:     file format elf64-x86-64


Disassembly of section .text:

00000000004000b0 <_start>:
  4000b0:	31 db                	xor    %ebx,%ebx
  4000b2:	b8 04 00 00 00       	mov    $0x4,%eax
  4000b7:	31 db                	xor    %ebx,%ebx
  4000b9:	ff c3                	inc    %ebx
  4000bb:	8d 0c 25 d4 00 60 00 	lea    0x6000d4,%ecx
  4000c2:	8b 14 25 e2 00 60 00 	mov    0x6000e2,%edx
  4000c9:	cd 80                	int    $0x80
  4000cb:	31 c0                	xor    %eax,%eax
  4000cd:	ff c0                	inc    %eax
  4000cf:	31 db                	xor    %ebx,%ebx
  4000d1:	cd 80                	int    $0x80

```

---

