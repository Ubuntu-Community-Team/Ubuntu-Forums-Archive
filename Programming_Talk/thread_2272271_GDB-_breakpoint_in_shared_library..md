---
title: "GDB- breakpoint in shared library."
date: 2015-04-05
forum: Programming Talk
---

### Post by mark152 on 2015-04-05
Hi guys. 
I have same problem as in this closed threat:  [http://ubuntuforums.org/showthread.php?t=2157293]("http://ubuntuforums.org/newthread.php?do=newthread&f=39"). 
And when complile it with option -fno-builtin then I can stop at strcpy function, but the output is actual different. It like this:
```

(gdb) list
1    #include<stdio.h>
2    #include<string.h>
3    main()
4    {
5        char a[20];
6        strcpy(a,"Hello, world!");
7        printf("%s\n",a);
8    }
(gdb) break strcpy
Breakpoint 1 at 0x8048370
(gdb) run
Starting program: /home/m/a.out 

Breakpoint 1, __strcpy_sse2 ()
    at ../sysdeps/i386/i686/multiarch/strcpy-sse2.S:1613
1613    ../sysdeps/i386/i686/multiarch/strcpy-sse2.S: No such file or directory.

```

So what is .../strcpy-sse2.S? Why it isn't something like .../libc.so as normal.
thanks for reading

---

### Post by xb12x2 on 2015-04-05
I think the following two links will do a good job explaining what is happening.

[http://stackoverflow.com/questions/13978692/strcpy-sse2-unaligned-s-not-found](http://stackoverflow.com/questions/13978692/strcpy-sse2-unaligned-s-not-found)

[https://sourceware.org/ml/libc-alpha/2013-09/msg00302.html](https://sourceware.org/ml/libc-alpha/2013-09/msg00302.html)

---

### Post by mark152 on 2015-04-06
@xb12c2: Thanks for your links.
I downloaded glibc source files (eglibc-2.19) and use `dir dirname` to indicate source file (that included strcpy), now everything ok. Ah, in the latter link I don't fully understand but I guess **strcpy-sse2** is improved version of **strcpy** function in libc shared library and now it is included in glibc source package, is it right?

---

