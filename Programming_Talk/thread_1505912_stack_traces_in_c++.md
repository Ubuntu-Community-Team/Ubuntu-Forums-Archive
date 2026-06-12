---
title: "stack traces in c++"
date: 2010-06-09
forum: Programming Talk
---

### Post by cph05a on 2010-06-09
I'm trying to find a way to get a stack trace with a list of function calls for debugging purposes. Unfortunately, I can't use gdb. I've attempted to use backtrace_symbols, but I end up getting only addresses from the executable (which makes sense I guess).
```

./prog(myfunc3+0x5c) [0x80487f0]
./prog [0x8048871]
./prog(myfunc+0x21) [0x8048894]
./prog(myfunc+0x1a) [0x804888d]
./prog(myfunc+0x1a) [0x804888d]
./prog(main+0x65) [0x80488fb]
/lib/libc.so.6(__libc_start_main+0xdc) [0xb7e38f9c]
./prog [0x8048711]

```
What I would really like to have is something more similar to the java printStackTrace() which gives the function names and line numbers of your source code. I'm guessing that it's just not possible in c++, but if anyone knows a way to accomplish this, the help it would be much appreciated. 

I'm using g++ (GCC) 4.1.2 20070925 (Red Hat 4.1.2-33)

---

### Post by trent.josephsen on 2010-06-09
Why no gdb?

---

### Post by Roptaty on 2010-06-09
> **cph05a said:**
> I'm trying to find a way to get a stack trace with a list of function calls for debugging purposes. Unfortunately, I can't use gdb. I've attempted to use backtrace_symbols, but I end up getting only addresses from the executable (which makes sense I guess).


Why cant you use GDB?

Have you compiled your source with -g flag?

---

### Post by cph05a on 2010-06-10
it's compiled with the -c flag

---

### Post by Roptaty on 2010-06-10
-c flag isn't the -g flag.

The -g flag will enable debugging symbols.
The -c flag will just compile the source file, and not link it.

---

### Post by Lux Perpetua on 2010-06-10
> **cph05a said:**
> it's compiled with the -c flagThat's irrelevant. 

Using -g will embed debugging information into your program so that you can debug it properly with GDB.

---

### Post by soltanis on 2010-06-10
> **Lux Perpetua said:**
> That's irrelevant. 

Using -g will embed debugging information into your program so that you can debug it properly with GDB.

+1

You must construct additional debugging symbols.

---

