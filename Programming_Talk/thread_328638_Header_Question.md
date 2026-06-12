---
title: "Header Question"
date: 2006-12-31
forum: Programming Talk
---

### Post by vze4p6c2 on 2006-12-31
Hey guys!!

Its a little question that I haven't been able to find in my C++ book.

When we type "#include <iostream>" #include "blah.h", how does the compiler knows where those files are?

Also how are the headers with <> and "" are different?

Thanks a lot guys, Vlad

---

### Post by thumper on 2006-12-31
The compiler looks in the INCLUDE_PATH.

<> and "" used to be different in whether or not they checked the current directory first prior to checking the INCLUDE_PATH, but most compilers (including gcc) don't do that any more.

---

### Post by Wybiral on 2006-12-31
Yeah, with gcc when you're compiling it, you may add directories to include using the "-I" flag, for instance if I had a header in the directory "/usr/include/whatever" I could add that directory for the compiler to check for something like this to compile it:
```

g++ myProgram.cpp -I/usr/include/whatever

```
You can add as many include path's as you'd like, just remember that the compiler will search for the files in order, so if you include the header "blah.h" and you add the directories "whatever1" and "whatever2" in this order...
```

g++ myProgram.cpp -I/usr/include/whatever1 -I/usr/include/whatever2

```
The "blah.h" located in "/usr/include/whatever1" will be used even if there is a "blah.h" in "/usr/include/whatever2" because it searches in the order that you add the directories.

---

### Post by vze4p6c2 on 2006-12-31
OK, thanks a lot, I got that.  Its just I can't seem to find the kernel srouces on my HD I already downloaded the kernel from the web.but didn't know how to include.

I see that INCLUDE_PATH is not a shell variable (typing cat $INCLUDE_PATH doesn't seem to work).  How may I alter the spot where it looks?

Vlad

---

