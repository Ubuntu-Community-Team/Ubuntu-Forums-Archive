---
title: "GDB -Check which line of code causing the SegFault err."
date: 2006-12-17
forum: Programming Talk
---

### Post by Andrea_44 on 2006-12-17
How do you check which line of a piece of C code causing a Segmentation Fault error message??

I have tried:
```

gcc -ggdb -o test test.c

(gdb) test
(gdb) run aaaaaaaa

Program received signal SIGSEGV, Segmentation fault.
0x0800632e in ?? ()
```

I was expecting to see somthing like:
```
(gdb) run aaaaaaaa

Program received signal SIGSEGV, Segmentation fault.
0x080483d8 in main (argc=-1208730400, argv=0x0) at test.c:12
12          copy(argv[1]);

```

How do you do that, or anything similar that could indicate which part of the code generate the error?

Thanks,
Andrea

---

### Post by lnostdal on 2006-12-17
> **Andrea_44 said:**
> How do you check which line of a piece of C code causing a Segmentation Fault error message??

I have tried:
```

gcc -ggdb -o test test.c

(gdb) test
(gdb) run aaaaaaaa

Program received signal SIGSEGV, Segmentation fault.
0x0800632e in ?? ()
```

I was expecting to see somthing like:
```
(gdb) run aaaaaaaa

Program received signal SIGSEGV, Segmentation fault.
0x080483d8 in main (argc=-1208730400, argv=0x0) at test.c:12
12          copy(argv[1]);

```

How do you do that, or anything similar that could indicate which part of the code generate the error?

Thanks,
Andrea

Type bt and press enter.

edit: Note that the libraries you use must also be compiled with debugging-symbols in them for you to be able to see where the segfault happens. Wheter this is important depends on what you're doing. :)

---

