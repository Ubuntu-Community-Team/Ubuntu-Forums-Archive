---
title: "Walking through many source files"
date: 2009-12-02
forum: Programming Talk
---

### Post by newport_j on 2009-12-02
This question is just basically a gdb question, although it is dealing with debugging cuda files. I believe it is still a gdb question.

I have compiled a file to debug. I used make dbg=1 and except for a few messages and warnings it, compiled and one can walk line by line through the first program. By that I mean the first file in the group.


matrixMul.cu matrixMul_kernel.cu matrix,h matrixMul.cpp   


Which is the source code for the program.

A simple make dbg=1 compiles this and it runs so I know that it is all stitched together specifically those first two *.cu files. I want to walk around the source code in matrixMul_kernel.cu and print varibles, watch variables etc.

When I load the compiled program like this:

cuda-gdb matrixMul

It loads perfectly. The problems comes in with the second file named matrixMul_kernel.cu., this is the file that contains a program called matrixMul which is basically a CUDA program. I am very interested in the program matrixMul that is in the computer file matrixMul_kernel.cu. 

When I ask it to break in at line in the program matrixMul it comes back with the question:


make breakpoint pending on future shared library load? (y or [n])?


I answer yes, but it means very little since the program does not stop at this new breakpoint it just runs to completion. Since it runs to completion I know that it has a complete executable.

I want it to stop in matrixMul at the beginning so I can wander around in the code seeing how cuda works in a matrix multiplication. It does not. I believe that somehow it is now finding matrixMul_kernel.cu, my second file of source code. The executable is whole, but the source is in more than one file. 

The question is how do I get into that program matrixMul_kernel.cu? 

As I said I use the command

cuda-gdb matrixMul

, but that does seems to load only the one main source file. I need all of the source files loaded.

Also, since I am in a CUDA program running with a CUDA card (the hardware), I have shut down xwindows.

Respectfully,

Newport_j

---

