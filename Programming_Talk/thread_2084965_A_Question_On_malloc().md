---
title: "A Question On malloc()"
date: 2012-11-17
forum: Programming Talk
---

### Post by 3246251196 on 2012-11-17
Hey guys. I am encountering a problem here and maybe someone can help. I am looking through the source code of a large old application. In one of the files, the program is trying to allocate memory using malloc, however a null pointer is constantly being returned. Just out of curiosity I changed the value of the size_t parameter to 1, so as to just allocated 1 byte of memory. The actual evaluation is ~~ 450 bytes. I guess my question is: is it either because malloc cannot find a contiguous section of memory on the heap or is it that there is no space left or is there a memory leak somewhere in the program? I have 8Gb of memory. Are there any tools I could use to test this? Valgrind? Or maybe someone can offer some different but more valid information as to what is happening...

Thanks.

---

### Post by MadCow108 on 2012-11-17
the most likely reason is an overflow in some part so that the argument to malloc ends up to be gigantic.
the easiest approach to debug it would probably be to reverse debug it with gdb.
[http://www.jayconrod.com/posts/28/tutorial-reverse-debugging-with-gdb-7](http://www.jayconrod.com/posts/28/tutorial-reverse-debugging-with-gdb-7)

valgrind can also help, but only if the reason is memory corruption or uninitialized use (valgrind --db-attach is tremendously useful).

---

### Post by 3246251196 on 2012-11-17
Thank you, Mad Cow. I will look into this later tonight.

I was evaluating the value of the argument and printf'ing it before I was passing it in as a parameter, and it was always coming up with the same value ~~ 456. But what you say could still hold true? That it somehow gains massive value right before malloc uses it?

---

### Post by MadCow108 on 2012-11-17
how does the memory usage behave until that point?
sar from systat can give some coarse estimates.

for more detailed analysis you can use massif which is included in valgrind.

I'm guessing that some memory corruption is the underlying cause, linux should always be able to overcommit 456 bytes at any time.
valgrind will help with that.

---

