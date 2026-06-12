---
title: "(GCC)Compile C into asm, hving the corresponding C code next to the asm, possible?"
date: 2006-10-13
forum: Programming Talk
---

### Post by Andrea_44 on 2006-10-13
Is there a parameter in GCC that allow you to compile
C into assembly, whilst also having the corresponding C 
code next to the generated assembly?

For example:
ubuntubox> gcc -S -?? helloworld.c

ubuntubox> cat helloworld.s
....
.globl main
        .type    main,@function
main:
        pushl %ebp
        movl %esp,%ebp
        pushl $.LC0
        call printf  /* printf("Hello, world!\n"); */
        addl $4,%esp
        xorl %eax,%eax
        jmp .L1
        leave       /*return 0;*/    
        ret

Something like that??


Many Thanks,

Andrea

---

### Post by toojays on 2006-10-13
If you compile with "-Wa,-adhln,-L -g -c", you get something like what you want coming up on stdout. (Courtesty of [http://sourceware.org/ml/crossgcc/2002-02/msg00019.html](http://sourceware.org/ml/crossgcc/2002-02/msg00019.html))

Also the -fverbose-asm flag can be useful if you just want to know what variable is allocated to what register.

---

### Post by Andrea_44 on 2006-10-14
Cheers~

Andrea

---

