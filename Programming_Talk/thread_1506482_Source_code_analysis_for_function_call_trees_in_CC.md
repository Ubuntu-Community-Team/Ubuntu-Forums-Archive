---
title: "Source code analysis for function call trees in C/C++/Fortran (possibly using gcc)"
date: 2010-06-10
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-10
I have been trying to find a resource that will allow me to read source code more easily by displaying the defined functions, classes, and structs in a tree based on which are dependent on which, allowing me to know which ones I should read first if I don't want to have to sift through mountains of code.  I don't mind if I have to write some code of my own to interpret it.

I didn't find any free linux tools to deal with this situation when I searched for it, but my idea would be to find out how to get this data out of gcc; it obviously has to do something like this, but man g++ is far too long for me to read so I don't know how to tell it to output the data (I am assuming the data would not be easily human-readable but (ideally) I could find out how to parse it and translate it with my own program)

---

### Post by DanielWaterworth on 2010-06-10
Take a look at clang and LLVM. Clang is a C compiler and it's internal structures are much easier to hack on.

---

### Post by MadCow108 on 2010-06-10
for such a purpose a profiler is more useful than looking at the internal structure of the compiler (look at all the -fdump flags of gcc, one of them should output the call graph).
callgrind in combination with kcachegrind can display nice call graphs.

callgrind is included in valgrind:
valgrind --tool=callgrind ./program
kcachegrind callgrind_output.file

of course you may not get all program paths when profiling only samples.

---

### Post by Zorgoth on 2010-06-10
valgrind died on one of my programs so I'm going with gcc's -fdump-ipa-cgraph option (thanks madcow!), but I still have some problems; I don't want my tree to be stuffed with standard library functions, and I don't want to manually list them all either.  It would be nice if I could find an automated command-line way to identify where a function was originally declared, since then I could distinguish code in /usr/include from other code.  Any ideas?

For Fortran the option doesn't seem to exist but the language is simple enough in this respect that I can probably parse the source code itself, certainly for the code I'm working with.

---

