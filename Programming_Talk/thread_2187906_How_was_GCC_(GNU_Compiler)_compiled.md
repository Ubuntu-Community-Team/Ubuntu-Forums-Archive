---
title: "How was GCC (GNU Compiler) compiled?"
date: 2013-11-14
forum: Programming Talk
---

### Post by sha1sum on 2013-11-14
Hello guys,

I'm learning the basics of programming and I've got a question. I've read that the program GCC (GNU compiler collection) is written in C++. But what I don't understand is, how did they compile it originally? How can you compile your compiler source code, if you haven't already compiled your compiler?

---

### Post by Tony Flury on 2013-11-14
It was almost certainly compiled/built with an earlier version of the compiler - which in turn was compiled with an earlier compiler .... Eventually you get to the first C++ compiler written in C - go back further, you get the first C compiler (written in Assembler), and even further back you get the first Assembler - written by hand in machine code.

---

### Post by sha1sum on 2013-11-14
I understand. Thanks!

---

### Post by r-senior on 2013-11-15
The process is known as bootstrapping:

[https://en.wikipedia.org/wiki/Bootstrapping_(compilers)](https://en.wikipedia.org/wiki/Bootstrapping_(compilers))

---

### Post by sha1sum on 2013-11-15
Thanks for that. Those guys who had to write that first assembler in machine code, must have had a very headache-giving  job.

---

### Post by llanitedave on 2013-11-16
There are some crazed geniuses in our past...

---

### Post by r-senior on 2013-11-16
> Those guys who had to write that first assembler in machine code, must have had a very headache-giving job.
Actually, writing an assembler in machine code is not a hugely difficult problem because, in its simplest form, an assembler just takes a symbolic representation of machine instructions and translates it into machine code

This is an example of 8080 assembly language from [https://en.wikipedia.org/wiki/Intel_8080:](https://en.wikipedia.org/wiki/Intel_8080:)

```
1000                        org     1000h       ;Origin at 1000h
1000            memcpy      public
1000  78        loop        mov     a,b         ;Test BC,
1001  B1                    ora     c           ;If (B or C) = 0,
1002  C8                    rz                  ;Return
1003  1A                    ldax    d           ;Load A from (DE)
1004  77                    mov     m,a         ;Store A into (HL)
1005  13                    inx     d           ;Increment DE
1006  23                    inx     h           ;Increment HL
1007  0B                    dcx     b           ;Decrement BC
1008  C3 00 10              jmp     loop        ;Repeat the loop
100B  
```

So "mov a,b" -> 78, "ora c" -> B1 and so on. It's a matter of reading a file, matching simple tokens and writing a file. Obviously non-trivial in machine code, but not mind-bending.

On simple processors, disassemblers are even simpler to write because it's just a matter of looking up numbers in a table and outputting sequences of characters, so 78 -> "mov a,b", B1 -> "ora c" and so on. There's no token matching. Disassemblers probably came before assemblers as a means of visualizing sequences of opcodes.

A much more difficult set of problems comes with a "high-level" programming language: lexical analysis, parsing, code generation and optimization. That was a big leap and spawned tools to help write compilers, like Lex and Yacc. Everything builds on everything else, which is the whole bootstrapping idea.

---

### Post by ssam on 2013-11-19
> **sha1sum said:**
> Thanks for that. Those guys who had to write that first assembler in machine code, must have had a very headache-giving  job.

If you are writing a compiler you need to know assembly pretty well anyway.

---

