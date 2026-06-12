---
title: "GL: Why is -lGL -lglut required for compiling?"
date: 2008-04-13
forum: Programming Talk
---

### Post by tehet on 2008-04-13
Hi,
How come you need to set these flags in order to compile stuff with GL and GLUT? Why is #include <GL/gl.h> and #include <GL/glut.h> not enough?

I think I have read an explanation for math.h and the -lm flag which perhaps has a similar cause but I can't find the explanation again.
Thanks

---

### Post by nvteighen on 2008-04-13
Because header files only include the protoypes of functions, not the functions themselves, which are defined in the proper shared library. In summary, those flags tell the linker (which is the 4th phase in the compiling process) which libraries are needed for that executable.

---

### Post by LaRoza on 2008-04-13
> **tehet said:**
> Hi,
How come you need to set these flags in order to compile stuff with GL and GLUT? Why is #include <GL/gl.h> and #include <GL/glut.h> not enough?

I think I have read an explanation for math.h and the -lm flag which perhaps has a similar cause but I can't find the explanation again.
Thanks

Look at the contents of gl.h and glut.h and you will see ;)

[http://en.wikipedia.org/wiki/Dynamic_linking#Dynamic_linking](http://en.wikipedia.org/wiki/Dynamic_linking#Dynamic_linking)

---

### Post by tehet on 2008-04-13
> **nvteighen said:**
> Because header files only include the protoypes of functions, not the functions themselves, which are defined in the proper shared library. In summary, those flags tell the linker (which is the 4th phase in the compiling process) which libraries are needed for that executable.
As opposed to, lets say, stdlib.h or does gcc silently link in glibc and such by default? Looking At gl.h, glut.h and stdlib.h I think I'm only seeing prototypes but then again, I'm kind of a noob.

---

### Post by LaRoza on 2008-04-13
> **tehet said:**
> As opposed to, lets say, stdlib.h or does gcc silently link in glibc and such by default? Looking At gl.h, glut.h and stdlib.h I think I'm only seeing prototypes but then again, I'm kind of a noob.

The standard library is statically linked (I think), so stdio.h declares the functions so the compiler will know how to handle the declarations. The definitions of the functions are already known.

All other libraries must be specified. The header needs to be found so the use of the functions can be determined by the compiler, and the library needs to be found for the linker.

---

### Post by tehet on 2008-04-13
Ah, I think I understand :)
Thanks nvteighen and LaRoza!

---

### Post by stroyan on 2008-04-13
gcc does link with libc by default.
You can see the link line by adding -v to the gcc options.
There is a -nodefaultlibs gcc option that will suppress the default use of libraries.

---

### Post by tehet on 2008-04-13
> **stroyan said:**
> gcc does link with libc by default.
You can see the link line by adding -v to the gcc options.
There is a -nodefaultlibs gcc option that will suppress the default use of libraries.
Compiling a small test program with -nodefaultlibs return
```
undefined reference to `printf'
```
so that confirms it. Thanks.

---

