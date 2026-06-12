---
title: "[SOLVED] yasm and GAS asm syntax"
date: 2008-07-04
forum: Programming Talk
---

### Post by WitchCraft on 2008-07-04
Question: If I compile the below program with: 
as hello.asm -o hello.o
ld hello.o -o hello

then it compiles and works fine.

If I try to use yasm, which should be compatible to GAS syntax:
yasm -p gas -f elf32 hello.asm -o hello.o
ld -o hello hello.o

I only get the following error:
hello.asm:2: label or instruction expected at start of line
What does that mean? I don't get it, what shall be incorrect ???
```

.section .data
 mystring: .ascii "Hello World!\n"
.section .text
.globl _start
_start:
    mov $4, %eax        # Syscall No. 4: = 'write'
    mov $1, %ebx        # File Descriptor
    mov $mystring, %ecx # Memory address of string
    mov $13, %edx       # strlen
    int $0x80           # call eax (=write), argument is memory address & strlen
    mov $1, %eax        # Syscall No. 1 = 'exit'
    mov $0, %ebx        # clear ebx
    int $0x80           # call eax (=exit), return value in ebx

```

---

### Post by henchman on 2008-07-05
wikipedia about GNU Assembler (GAS)
> One source of criticism is the fact that on the x86 and x86-64 architecture it uses the AT&T assembler syntax, rather than the Intel syntax

wikipedia about Yasm
> Yasm is a software program that attempts to be a complete rewrite of the NASM assembler. 

wikipedia about NASM
```
NASM uses Intel assembly syntax instead of AT&T syntax.
```

well, if i don't get it wrong, it means that GAS uses AT&T syntax while YASM uses the Intel syntax, because its a clone of NASM which uses it.

cya :)

---

### Post by WitchCraft on 2008-07-05
yasm should have support for GAS assembly (AT&T syntax)

as you can see in my yasm directive:
yasm **-p gas** -f elf32 hello.asm -o hello.o

-p gas should enable GAS syntax. And it does, if I just comment out line 2, but then I don't have the string...

---

### Post by WitchCraft on 2008-07-06
bump.

---

### Post by NathanB on 2008-07-06
Hmm... I changed this...
[php].section .data
 mystring: .ascii "Hello World!\n"
[/php]
...to this...
[php].section .data
 mystring:
 .ascii "Hello World!\n"
[/php]
...and it assembled with version (0.5.0).  But a 'readelf' shows me that it didn't set the section flags correctly... so it won't execute.  Yasm is under extensive development currently, so we need to test the latest version and file any bug reports here:

[http://www.tortall.net/projects/yasm/](http://www.tortall.net/projects/yasm/)

Nathan.

---

### Post by WitchCraft on 2008-07-07
> **NathanB said:**
> Hmm... I changed this...
[php].section .data
 mystring: .ascii "Hello World!\n"
[/php]
...to this...
[php].section .data
 mystring:
 .ascii "Hello World!\n"
[/php]
...and it assembled with version (0.5.0).  But a 'readelf' shows me that it didn't set the section flags correctly... so it won't execute.  Yasm is under extensive development currently, so we need to test the latest version and file any bug reports here:

[http://www.tortall.net/projects/yasm/](http://www.tortall.net/projects/yasm/)

Nathan.

will file the bug report.
In the mean time I also got it to work with yasm with a few mods, and gdb could find the offsets but it segfaulted when run...

one file linked to glibc also didn't execute, but there it always outputted the error message "file not found" (but the file was there...)...

---

