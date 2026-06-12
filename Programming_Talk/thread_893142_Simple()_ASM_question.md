---
title: "Simple(?) ASM question"
date: 2008-08-18
forum: Programming Talk
---

### Post by qikink on 2008-08-18
I'm trying to find a way to profile code that I have written in assembly, but every tutorial I can find says to put -p in the command line arguments to my compiler. NASM does not use -p in this way, and for the life of me I can't figure out how to include profiling information with NASM. Hopefully someone knows what I'm talking about, and can tell me either how to assemble with gcc, or include profiling information with NASM, or even just point me towards a different profiling utility.

---

### Post by jinksys on 2008-08-18
Can't you just let NASM compile your assembly into an elf and then use GCC to include the gprof profiling code?

For example:
Let's say I have this code...
```


SECTION .data           ; data section
msg:    db "Hello World",10     ; the string to print, 10=cr
len:    equ $-msg               ; "$" means "here"
                                ; len is a value, not an address

        SECTION .text           ; code section
        global main             ; make label available to linker
main:                           ; standard  gcc  entry point

        mov     edx,len         ; arg3, length of string to print
        mov     ecx,msg         ; arg2, pointer to string
        mov     ebx,1           ; arg1, where to write, screen
        mov     eax,4           ; write sysout command to int 80 hex
        int     0x80            ; interrupt 80 hex, call kernel
ret

```

Then compile it...

```


$ nasm -f elf mycode.asm 
$ gcc -pg mycode.o -o mycode
then create profile data
$./mycode
$gprof mycode

```

If your entire application is written using NASM, then make sure it terminates using exit(), or by main returning, or your gmon.out file won't be created.

---

