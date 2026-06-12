---
title: "interesting segmentation fault: why?"
date: 2011-12-31
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-12-31
Going through the process of learning C, and I thought it would be interesting to write a program that looped indefinitely, and recursively, like this:

```

#include <stdlib.h>

void hello() {
     printf("hello");
     //calls itself.
     hello();
}

main() {
     //launches hello() intially
     hello();
}
```

Now..obviously, this loops itself indefinitely. But it doesn't. It runs for roughly 10 seconds, as expected (hellohellohellohello) but then segfaults. Why? As far as I can see, it has accessed no memory it shouldn't.

More of a 'I can use, but don't understand' question than a problem as such.

Would this happen in any other compiled language?

---

### Post by perperNorbi on 2011-12-31
1) The real reason of the segfault is a stack overflow.
2) printf is buffered, and flushed only after line breaks (or a huge amount of characters).

---

### Post by MadCow108 on 2011-12-31
each function call places something on the stack, to the very least a return address.
when you recurse indefinitly you run out of stack very fast (see ulimit -s for the default size)

the printf buffer has nothing to do with the crash, its large (~4mb probably) and lies in the heap which is only limited by available virtual memory.

---

### Post by Bachstelze on 2011-12-31
Also...

> **MG&TL said:**
> 
Would this happen in any other compiled language?

It's not really a matter of language, but of platform. It is perfectly conceivable to build a computer that would use other mechanisms than a stack for function calls, and on which this code would run fine. If we limit ourselves to the IA32 architecture, the answer is no, though that doesn't really mean anything. For example in Haskell:

```
foo :: IO ()

foo = do
        putStrLn "Hello, world!"
        foo

main = do
        foo

```

This runs indefinitely and the memory usage remains constant so it is a safe bet to say that it will keep running (though I'm not 100% sure of this). I say this does not mean anything because functions in C and in Haskell are fundamentally different.

---

### Post by ofnuts on 2011-12-31
> **MG&TL said:**
> Going through the process of learning C, and I thought it would be interesting to write a program that looped indefinitely, and recursively, like this:

```

#include <stdlib.h>

void hello() {
     printf("hello");
     //calls itself.
     hello();
}

main() {
     //launches hello() intially
     hello();
}
```Now..obviously, this loops itself indefinitely. But it doesn't. It runs for roughly 10 seconds, as expected (hellohellohellohello) but then segfaults. Why? As far as I can see, it has accessed no memory it shouldn't.

More of a 'I can use, but don't understand' question than a problem as such.

Would this happen in any other compiled language?
Compile and run this:
```

#include <stdio.h>

int level=0;
int maxlevel=10;

void recursive() {
    int thislevel=++level; // address used to locate stack frame
    printf("A level %d, stack frame at %p\n", thislevel, &thislevel);
    if (thislevel < maxlevel) {
        recursive();
    }
    return;
}

int main() {
    recursive();
    return 0;
}

```
You'll see that each level takes 0x30 bytes (48...) on the stack (this would be 44 without the "thislevel" variable). By default on Linux the stack size is 8Mbytes (see "ulimit" command) which means that you overflow the stack in at most 190K recursive calls.

---

### Post by MG&amp;TL on 2011-12-31
> **Bachstelze said:**
> Also...



It's not really a matter of language, but of platform. It is perfectly conceivable to build a computer that would use other mechanisms than a stack for function calls, and on which this code would run fine. If we limit ourselves to the IA32 architecture, the answer is no, though that doesn't really mean anything. For example in Haskell:

```
foo :: IO ()

foo = do
        putStrLn "Hello, world!"
        foo

main = do
        foo

```

This runs indefinitely and the memory usage remains constant so it is a safe bet to say that it will keep running (though I'm not 100% sure of this). I say this does not mean anything because functions in C and in Haskell are fundamentally different.

Thanks Bachstelze and MadCow; brilliant answers. I shall just have to be careful of recursive functions-bachstelze-you mention that the haskell function above will run fine because it's not a C function-does that mean a different form of recursion (goto loop?) would work?

---

### Post by Barrucadu on 2011-12-31
If you compile that with -O2, -O3, -Os, or just -foptimize-sibling-calls, passed to GCC, it performs tail-call optimisation (the same method used in Scheme systems, probably Common Lisp and Haskell too) and it does run indefinitely.

---

### Post by cgroza on 2012-01-01
Many functional languages like Haskell implement tail call optimization which makes the function to recurse in constant space.

But sometimes, tail call optimization is not possible on some code, because the way the code is written forces the compiler to keep a separate reference for some particular value at each call.
Usually, it can be fixed by using some accumulator function parameter.

---

### Post by MG&amp;TL on 2012-01-02
Thanks for all of those answers guys, I've done some googling, and I think I get it now. :)

---

