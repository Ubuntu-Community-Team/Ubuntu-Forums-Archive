---
title: "How to include flags in Anjuta"
date: 2008-02-07
forum: Programming Talk
---

### Post by fulgencio on 2008-02-07
Hi,
I downloaded the CImg-dev package with synaptics a few days ago. I was able to compile all the examples perfectly using the line in the terminal:
[PHP] g++ -o CImg_demo.exe CImg_demo.cpp -O2 -L/usr/X11R6/lib -lm -lpthread -lX11
[/PHP]

but I'm interested in compiling this and other code in **Anjuta IDE** , but When I paste examples code in a new project , although It compiles perfectly, when I try to build I get hundreds of error messages. I believe it has something to do with the flags I'm not able to give to anjuta. any help???

thanks in advance

Luis Berlioz

---

### Post by fulgencio on 2008-02-07
Hi there, 
all the errors I get while building (when I use the build command)
have similar form some examples are:

[PHP]
 undefined reference to `XDestroyWindow'
 undefined reference to `XFreeColormap'
 undefined reference to `XSync'
undefined reference to `pthread_cancel'
 undefined reference to `pthread_join'
 undefined reference to `XSync'
 undefined reference to `XCloseDisplay'

[/PHP]

---

### Post by Sammyf on 2008-02-09
A libraryyou need is not linked at build time. Somehow the devs  changed the way you can include libraries in your projects in Anjuta and I couldn't find a way to add them except by adding them manually in the Makefile (which somehow beats the notion of an IDE :/

---

### Post by fulgencio on 2008-02-09
Thanks, for the answer, but can you tell me how to include this libraries manually, I've taken a look at the manual and couldn't find any answers. I really don't need instructions for my specific problem just a general instruction that works!!
thanks in advance

---

