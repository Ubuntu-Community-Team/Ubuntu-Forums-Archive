---
title: "ICC C++ Compilation"
date: 2006-04-04
forum: Programming Talk
---

### Post by Lightmywifire on 2006-04-04
Hey there,
    I'm having some trouble compiling C++ code with ICC. It appears to be having a problem linking a number of object files together while creating an executable file.

The compile line I'm using is:
icc -o simple_server ServerSocket.o Socket.o simple_server_main.o

I get a good number of what appear to be linking errors, so I tried:
icc -x c++ -o simple_server ServerSocket.o Socket.o simple_server_main.o

I also get errors, but there are too many check through and writes past my terminal buffer anyway. 

---------------------------------------------------------------------------------------

Ok, in the middle of this post i found the answer, but ill post it anyway just because there's gotta be someone else out there that will use ICC at some point and this forum doesn't have enough ICC topics.

To compile a C++ file, the command is just slightly different. It uses the icpc command. So instead of icc, you simply use icpc and compile like you would if i you were using GCC/G++. 

example:
icpc -o simple_server ServerSocket.o Socket.o simple_server_main.o

No more linking problems :)

---

