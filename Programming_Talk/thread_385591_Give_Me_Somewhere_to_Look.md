---
title: "Give Me Somewhere to Look"
date: 2007-03-15
forum: Programming Talk
---

### Post by prodonjs on 2007-03-15
I'm currently doing work on a senior culminating experience software development project. My partner and I are working to implement an updated, and hopefully more efficient algorithm for calculating the greatest common divisor of 2 arbitrary precision numbers in the GMP library.

We've currently hit a roadblock in our testing because we have a bug that seems to be as elusive as a needle in a haystack. Basically, when we are testing on a particular type of random number (ones with long strings of 0s and 1s in their binary representation, since these are the most likely to catch corner case bugs), we get a segmentation fault that crashes the program.

The interesting thing about this is that the timing of the segmentation fault has a lot to do with how many print statements are being executed. If all of them are disabled (via a preprocessor statement), then the program will segfault significantly earlier than if they are all enabled.

So basically, the program is a ticking time bomb and obviously there must be some kind of memory over-run occuring, and the addition of the print statements is off-setting values on the stack far enough to delay the problem.

The only problem is that tracking this error is a beast. Since I am linking against the dynamic libgmp.la file using libtool, GDB is being much help. Often, the segfault is occuring in some other function but I know the function of concern is the gcd.c file we are working with.

I'm sort of at a loss for the next step, but I wondered if anyone else had maybe had some experience with segmentation faults that seem to be contingent on extra 'junk' information going onto the stack.

I have used these print statements to determine the locations and ranges of all my pertinent data, and it all seems to be fine; no apparent overlap. My team and my advisor are all temporarily stumped with this. There are no problems at all using the exact same test program, and the original version of the gcd.c file that is in the GMP library currently. Anyone care to venture a guess?

---

### Post by rplantz on 2007-03-16
I would look at compiler versions. Argument passing protocols have changed significantly around version 4.0 of gcc. I haven't kept track of everything, so I can't give any details. But I know that when I look at the assembly language generated from a C function (using -S), stack manipulations at function entry and exit are very different than in pre-4.0 versions.

---

### Post by amo-ej1 on 2007-03-16
How far does valgrind bring you ? 

> 
Memcheck

Memcheck detects memory-management problems, and is aimed primarily at C and C++ programs. When a program is run under Memcheck's supervision, all reads and writes of memory are checked, and calls to malloc/new/free/delete are intercepted. As a result, Memcheck can detect if your program:

    * Accesses memory it shouldn't (areas not yet allocated, areas that have been freed, areas past the end of heap blocks, inaccessible areas of the stack).
    * Uses uninitialised values in dangerous ways.
    * Leaks memory.


see valgrind.org for more info, might proof helpful in this situation.

When this isn't helpfull personally i'd start rebuilding the application from scratch, pasting in existing code to determine when the issue exists.

---

### Post by prodonjs on 2007-03-17
OK, I am getting somewhere. I had to figure out how to rebuild the library using static libraries instead of shared ones.

That lets me get symbol table information from the module I need to see. It appears like I'm segfaulting because at least one of the pointers I am accessing gets it value set to inaddressable regions of memory (very low regions below address 0x100. Obviously, somewhere the value of the pointer is changing without my knowledge.

However as I have said, this problem did not occur on 200,000 inputs of 4096 bit integers (as well as various other ranges). It only occurs whenever I try to use these particular types of randomly generated numbers with long strings of 1s and 0s. It seems highly odd, but there must be something about this particular type of data that causes problems.

What I need to be able to do is see where this side-effect of reassigning a pointer in memory comes at. Is there a way to use GDB to flag a variable and note when its value changes?

---

