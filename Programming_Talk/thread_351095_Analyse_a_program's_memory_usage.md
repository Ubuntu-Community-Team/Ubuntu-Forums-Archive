---
title: "Analyse a program's memory usage?"
date: 2007-02-01
forum: Programming Talk
---

### Post by tomane on 2007-02-01
Hello,

This isn't really a programming question but folks around here are probably the most capable of handling my doubt :)
Is there some tool that I can use to "measure" how much memory a program is consuming?Being able to get that information in a per-funcion basis would be a big plus.
I already tried valgring but it seems to only show information about malloc'ed memory, and I don't use mallocs at all.
I'm writing it in C, and using gcc4.1.2 to compile.

Thanks in advance :)

Cheers,
--to

---

### Post by winch on 2007-02-01
If your not allocating memory dynamically it will either be allocated [statically]("http://en.wikipedia.org/wiki/Static_memory_allocation") in the executable image at compile time or [automatically]("http://en.wikipedia.org/wiki/Automatic_memory_allocation") on the stack at run time.

Both the exe size and the stack are essentially a fixed size for the duration the program is running so your program is always using the same amount of memory.

Are the usual tools like [top]("http://www.mcsr.olemiss.edu/cgi-bin/man-cgi?top+1") not enough? Have your tried a [profiler]("http://en.wikipedia.org/wiki/Profiler_%28computer_science%29") like [gprof]("http://www.gnu.org/software/binutils/manual/gprof-2.9.1/html_chapter/gprof_toc.html")?

---

### Post by tomane on 2007-02-01
Well, yes, the program has parts that are automatically allocated and others that are statically allocated, some of wich even have initialization data, but that's nothing new, so far.

top isn't very handy because the program runs only for a short ammount of time and also because it would be really nice to know which functions eat more ram and which don't.
I don't know a lot about gprof but have already used it. I thought it analysed only timing related aspects, not memory related. Is it possible to use gprof to get this info?

cheers,
--to

---

### Post by Houman on 2007-02-01
hi there;

One of the more popular tools is valgrind [http://en.wikipedia.org/wiki/Valgrind](http://en.wikipedia.org/wiki/Valgrind), and its in teh repositories.

regards

Houman

---

### Post by tomane on 2007-02-01
Today I had a small run with valgrind with the memcheck tool. It looked like to track only dynamic allocation of memory and usage of uninitialized data and I didn't look for more info on valgrind. Perhaps it can do a bit more than that, I'll see it tomorrow in the morning.

Thanks for the help
cheers,
--to

---

### Post by winch on 2007-02-02
> **tomane said:**
> Well, yes, the program has parts that are automatically allocated and others that are statically allocated, some of wich even have initialization data, but that's nothing new, so far.

This gives you some indication of how much stack space a function uses for automatic variables.
[http://www.kegel.com/stackcheck/#static](http://www.kegel.com/stackcheck/#static)

For the static allocated stuff the size of the executable should give an indication. objdump can probably also show you the sizes of individual sections within the executable.

---

### Post by tomane on 2007-02-02
Thanks for all replies, folks :)
That little program in kegel.com is quite handy indeed.
I'm also using valgrind with the massif tool, which gives me just what I wanted :D

cheers,
--to

---

### Post by kuscsik on 2007-10-08
I prefer to use gprof. I wrote a nice example

[http://kuscsik.blogspot.com/2007/08/how-to-benchmark-c-code-using-gcc.html]("http://kuscsik.blogspot.com/2007/08/how-to-benchmark-c-code-using-gcc.html")

---

### Post by tomane on 2007-10-08
> **kuscsik said:**
> I prefer to use gprof. I wrote a nice example

[http://kuscsik.blogspot.com/2007/08/how-to-benchmark-c-code-using-gcc.html](http://kuscsik.blogspot.com/2007/08/how-to-benchmark-c-code-using-gcc.html)
That's for measuring the time spent on each function during program execution, not for getting an idea of the memory used by each function or by the whole program.

--to

---

