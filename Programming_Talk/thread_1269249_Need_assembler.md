---
title: "Need assembler"
date: 2009-09-18
forum: Programming Talk
---

### Post by stallvalds on 2009-09-18
Hello everybody,
I'm taking a microprocessors class and was wondering if there was a good assembler for Jaunty. I need it to be able to assemble, link, and debug. I'm using an old Borland program to do this in windows. I think it's TASM, Tlinker, and Turbo debugger. Is there an alternative for Ubuntu? I'm wondering if the Borland programs will run under dosbox or wine?

---

### Post by slavik on 2009-09-18
nasm

---

### Post by stallvalds on 2009-09-18
Please forgive my noobishness, but is that an all-in one package that will assemble, link, and debug?

---

### Post by mmix on 2009-09-18
yasm

[quote="[yasm](http://www.tortall.net/projects/yasm/)"]
Key Current User-Visible Features

    * Nearly feature-complete lexing and parsing of NASM syntax.
    [color=red]* Basic support for TASM syntax.[/color]
    * Nearly feature-complete lexing and parsing of GAS (GNU assembler) syntax.
    * AMD64 support (enabled using "BITS 64", "-m amd64", or selecting an explicitly 64-bit object format output such as "-f win64" or "-f elf64")
    * 64-bit (and larger) integer constants allowed (including math operations).
    * A fast jump size optimizer equivalent to or better than other assemblers' multi-pass optimizers.
    * Support for multiple object formats:
          o Binary object file output (NASM style).
          o COFF object file? output, for use with DJGPP.
          o Win32 object file? output.
          o Win64/AMD64 aka "x64" object file? output.
                + Supports structured exception handling 
          o RDOFF2 object file? output.
          o ELF32 and ELF64 object file output.
          o 32 and 64-bit Mach-O object file? output. 
    * STABS, DWARF2, and CodeView? debug formats.
    * Portability; currently compilable on:
          o UNIX and compatibles (32-bit and 64-bit FreeBSD and Linux tested, GNU configure based autoconfiguration)
          o DOS (using DJGPP)
          o Windows (using Visual C++ or CygWin). 
    * Internationalization support via GNU gettext. 
[/quote]

---

### Post by c0mput3r_n3rD on 2009-09-18
Just be careful because programming assembly in winblows and programming assembly in Linux can be very different.

```

.386
.model flat, STDCALL

.data
    message db  "HelloWorld!$"
.code

org 100h

start:

    mov edx, offset message
    mov ah, 09
    int 21h
    mov ax, 4c00h
    int 21h
    
end start

```[http://www.tek-tips.com/viewthread.cfm?qid=627433&page=19](http://www.tek-tips.com/viewthread.cfm?qid=627433&page=19)

Compared to:
```

section data:
    hello:        db 'Hello World!',10
    helloLen:   equ $-hello

section text:
    global _start

_start:
    mov eax, 4        
    mov ebx, 1        
    mov ecx, hello        
    mov edx, helloLen    
    int 80h          
    
    mov eax, 1       
    mov ebx, 0       
    int 80h            

```

---

### Post by falconindy on 2009-09-18
Wow, TASM. Didn't think anyone still had a copy of that around. I'm taking an assembly class this semester as well. I put in some time over the summer playing around with a few assembers in preparation. Things I've learned (and might be of some help to you):

**NASM** - Netwide Assembler. I'm taking a guess, but I suspect this is the most popular assembler for Linux. It's in the repositories if you don't already have it and by default, Ubuntu has a linker included (man ld). If you're on a 64 bit system, assembling 32 bit code is a little tricky, but very feasible. I've setup a 32-bit chroot for myself and rather than fight with assembler/linker options, I just do all my bidness in this chroot.

**AS** - Uses AT&T's "GAS" syntax. Haven't played with this much, but I figured I'd mention that it's out there. I suspect this has dwindled somewhat in popularity, but still maintains somewhat of a following.

**MASM** - Microsoft Assembler. I hate this with a firey passion, and I spent most of my last class making calls to interrupt 92h and 19h in an attempt to crash the workstation I was on. This code can be assembled on Ubuntu using JWasm, but you'll need to link the object with LINK.EXE or LINK32.EXE on Windows. It works great through VirtualBox if you can't get your hands on the actual MASM assembler (which also works great through VBox).

**In General** - The basic layout of an assembly file is always going to be different based on the assembler you're using. Directives and declarations may be different (as illustrated by c0mput3r_n3rD), but the instructions such as mov, int, add, or sub will always be the same since it's hardware dependent.

---

### Post by stallvalds on 2009-09-18
I am only programming for an 8086. A simple 16 bit microprocessor. Are the names of the registers different in Linux (ax, dx, etc.)? I hope there's not too many differences. I figured In Linux I couldn't end  my code with int21h, as that returns to a DOS command prompt, but other than that, how different can it be? I could use some more input from everyone. If there are major differences, I may just stick with M$ for my assembly.

---

### Post by falconindy on 2009-09-18
You have 4 registers when writing assembly: a, b, c, and d. If you're programming for only 16 bit, they're accessible as: ax, bx, cx, and dx. You** also** have the ability to only access half of the 16 bit registers, either the higher or lower order 8 bits. Those can be referenced as al ('a' low), ah ('a' high), bl, bh, etc. You'll find that this is handy because you move your variables into the approriate size register. That is, you can't declare a byte and move it into the ax register -- you'd need to declare a word.

The only difference in 32 bit assembly is that you have access to 32 bit registers, named eax, ebx, ecx, and edx. You have no ability to access the high order 16 bits separately like you do with the lower 16 bits.

In linux, the equivalent of 'int 21h' is 'int 80h'.

---

### Post by slavik on 2009-09-18
in "windows" there are 2-3 interrupts to handle systems calls (10h is another one), in Linux, all system calls are 80h (there isn't anything else either) and the first argument (what call to make) always goes into ax, first arg to the call into bx and so on, if there are more than 6 args, you create a list and give the address to the list in bx.

long story short: assembly in linux is more organised when it comes to syscalls.

---

### Post by falconindy on 2009-09-18
> **slavik said:**
> in "windows" there are 2-3 interrupts to handle systems calls (10h is another one), in Linux, all system calls are 80h (there isn't anything else either) and the first argument (what call to make) always goes into ax, **first arg to the call into bx and so on, if there are more than 6 args, you create a list and give the address to the list in bx.**

long story short: assembly in linux is more organised when it comes to syscalls.
I understand that the call goes into ax, but if you want to specify 6 arguments, aren't you referencing bh, bl, ch, cl, dh, dl? Are you allowed to use entire 16 bit registers for args?

Or am I missing something?

---

### Post by slavik on 2009-09-18
The argument must be in bx, not strictly bl or bh. Not sure why there is confusion.

from : [http://www.cin.ufpe.br/~if817/arquivos/asmtut/index.html](http://www.cin.ufpe.br/~if817/arquivos/asmtut/index.html)
> 
Linux system calls are called in exactly the same way as DOS system calls:

   1. You put the system call number in EAX (we're dealing with 32-bit registers here, remember)
   2. You set up the arguments to the system call in EBX, ECX, etc.
   3. You call the relevant interrupt (for DOS, 21h; for Linux, 80h)
   4. The result is usually returned in EAX 

There are six registers that are used for the arguments that the system call takes. The first argument goes in EBX, the second in ECX, then EDX, ESI, EDI, and finally EBP, if there are so many. If there are more than six arguments, EBX must contain the memory location where the list of arguments is stored - but don't worry about this because it's unlikely that you'll use a syscall with more than six arguments. The wonderful thing about this scheme is that Linux uses it consistently &#8211; all system calls are designed this way, there are no confusing exceptions.

---

### Post by falconindy on 2009-09-18
> **slavik said:**
> The argument must be in bx, not strictly bl or bh. Not sure why there is confusion.

from : [http://www.cin.ufpe.br/~if817/arquivos/asmtut/index.html](http://www.cin.ufpe.br/~if817/arquivos/asmtut/index.html)
I guess I'm confused because I'm not familiar with ESI, EDI, and EBP being used in a 32-bit context.

---

### Post by slavik on 2009-09-19
they are just registers.

and forget about ah, al and the such ... nobody does that anymore. focus on eax and such and even rax (if you have a 64bit machine).

---

