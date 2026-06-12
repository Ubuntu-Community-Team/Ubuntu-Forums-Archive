---
title: "Printing values from __jmp_buf and printing stack contents?"
date: 2009-05-05
forum: Programming Talk
---

### Post by Glavata on 2009-05-05
Hello, my goals are to print every member of a jmp_buf struct and also print the contents of my stack when I call setjmp(env) in C.

I have declared jmp_buf env; and inside a function I have a call to setjmp(env); Following the header files, /usr/include/setjmp.h I saw that struct __jmp_buf_tag has a __jmp_buf member which is defined in /usr/include/bits/setjmp.h. My machine is not 64bit so I saw that __jmp_buf is defined as an array of ints of lenth 6 (typedef int __jmp_buf[6];). So from this I was able to print all the members inside 'env' in hex:

        printf("%x\n", env[0].__jmpbuf[0]);
        printf("%x\n", env[0].__jmpbuf[1]);
        printf("%x\n", env[0].__jmpbuf[2]);
        printf("%x\n", env[0].__jmpbuf[3]);
        printf("%x\n", env[0].__jmpbuf[4]);
        printf("%x\n", env[0].__jmpbuf[5]);

What one of my questions is what do each of these addresses point to? I assume some are registers, others something else. I was unable to find documentation for what each of them meant. Also from this point on, how would I go about printing the entire stack of my program at the state when setjmp(env) was called?

Thank You!

---

### Post by bapoumba on 2009-05-05
Moved to PT :)

---

