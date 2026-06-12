---
title: "GCC -march=native -mtune=native"
date: 2009-02-28
forum: Packaging and Compiling Programs
---

### Post by Nullack on 2009-02-28
Gday,

So when I use native for march and mtune, will the compiler automatically use sse, sse2, mmx and so on if my processor supports it?

Am I required to specify both march and mtune together?

I'm doing some experiments with the command:

gcc -march=native -mtune=native -O3 -Wall -pipe -o hello hello.c

---

### Post by cyfur01 on 2009-02-28
Regarding sse, I've read accounts going both ways. 

However, if you run gcc with the '-S' flag, it will spew out the assembler code in a '.s' file. This file begins with a header which lists the options gcc used. Thus, you can see if it picks up the sse options as you wished. (Running v4.3.2, mine appears to have detected sse without me explicitly specifying it.)

Regarding '-march' and '-mtune', I've tried compiling with different combinations of '-mtune' and '-march', and it appears that '-march' over-rules '-mtune' (i.e., compiling with both or just '-march' resulted in the same assembler file, but running with just mtune resulted in some differences.)

---

### Post by Nullack on 2009-02-28
Great, thanks :)

---

### Post by Dragonfi on 2011-05-27
Hi, I know it's probably a bit late, but at least I can help out others who stumble into this thread.

You can see the actual flags gcc use, by using the -Q -v options.
```
gcc -march=native -Q -v source.c
```

Actually, when you use -march=native, GCC usually sets -mtune to the appropriate value (at least on my machine it works that way). So, there is no reason to set -mtune if you already set -march.

Source/Further reading:
[Gentoo has a good read about gcc optimizations.]("http://www.gentoo.org/doc/en/gcc-optimization.xml")

---

