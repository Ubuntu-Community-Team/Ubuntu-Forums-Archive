---
title: "Compiling"
date: 2008-02-26
forum: Programming Talk
---

### Post by Suisidal Monkey on 2008-02-26
I am in a c++ programming class that uses windows instead of Linux, so there is no help for me.

We use graphics files from the book we use to create graphics applications. I can get my code to compile in the terminal with the command

g++ *filename.cpp* ccc_x11.cpp ccc_shap.cpp -L /usr/X11R6/lib -lX11 -o program

How do I either link the files correctly or tell kdevelope to use these arguments in compiling them. I have put the 4 files from the book into the source directory. It seems to be that the compiler is not linking to the /usr/X11R6/lib, because the compile errors look like this:

/home/bwyckoff/Documents/PIC_10A/hw6/src/ccc_x11.cpp:292: undefined reference to `XTextExtents'
/home/bwyckoff/Documents/PIC_10A/hw6/src/ccc_x11.cpp:299: undefined reference to `XClearArea'
/home/bwyckoff/Documents/PIC_10A/hw6/src/ccc_x11.cpp:301: undefined reference to `XSetForeground'
/home/bwyckoff/Documents/PIC_10A/hw6/src/ccc_x11.cpp:302: undefined reference to `XDrawImageString'
/home/bwyckoff/Documents/PIC_10A/hw6/src/ccc_x11.cpp:305: undefined reference to `XDrawLine'

thank you in advance

---

### Post by geraldm on 2008-02-26
Need to include the header files ?
insert into the command line:
-I/usr/include/X11

Gerald

---

