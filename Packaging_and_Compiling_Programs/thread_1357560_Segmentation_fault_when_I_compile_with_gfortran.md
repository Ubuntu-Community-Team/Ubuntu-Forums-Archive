---
title: "Segmentation fault when I compile with gfortran"
date: 2009-12-17
forum: Packaging and Compiling Programs
---

### Post by kgb3233 on 2009-12-17
Hi. I have recently experienced a STRANGE thing while i compile a CFD code with gfortran.

 When i added following line in code, it works without any problem.

 ```
print *, 'Check point'
```

 However, when i delete above line then the program prints out 'Segmentation fault' and it stops.

 I cannot understand why this happened since the line i added and deleted does nothing in my code at all!

 Is there anyone who has encountered this problem before?

 Please help me!! orz

---

### Post by Some Penguin on 2009-12-17
'print' does change state; it pushes and pops stack frames, and touches other resources (the IO, after all).  What you have is symptomatic of memory corruption prior to the print.  Fire up a debugger, check the stack trace,  check what memory access is blowing up, and look from there.  Perhaps look into Valgrind and the like (Electric Fence, Purify, et al).

---

### Post by jabl on 2010-01-03
Compile with the "-g -Wall -pedantic -fbounds-check" options, fix all problems you encounter, then run it through valgrind; as already mentioned your problems strongly hints at a memory corruption issues, usually caused by a array bounds bug.

---

