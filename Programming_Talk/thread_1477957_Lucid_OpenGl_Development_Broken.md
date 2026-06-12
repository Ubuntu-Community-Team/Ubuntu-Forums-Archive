---
title: "Lucid OpenGl Development Broken"
date: 2010-05-09
forum: Programming Talk
---

### Post by dev.konverje on 2010-05-09
Hi, 

I am a ubuntu user for over two years now. As part of my education, i was learning OpenGL programming using the GLUT (utility toolkit).

Hence i had installed the required libraries eg. mesa GL GLU freeglut, etc in karmic.
And my programs worked flawlessly.

When lucid was released, i did an upgrade, and now i suppose glu is broken.

the following errors and being displayed when i compile, ( i guess the problem lies in the linker stage)

```
$ gcc CG_LP2.cpp -lglut
/tmp/ccqk7QHP.o: In function `myinit()':
CG_LP2.cpp:(.text+0x683): undefined reference to `gluOrtho2D'
/tmp/ccqk7QHP.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```any suggestions as to how to workaround it or a possible fix, will be welcome...

i have attached the CG_LP2.cpp file

---

### Post by Zugzwang on 2010-05-09
You need to compile C++ programs with "g++" and not "gcc".

---

### Post by dev.konverje on 2010-05-09
> **Zugzwang said:**
> You need to compile C++ programs with "g++" and not "gcc".

g++ is just alias for gcc, gcc is the actual compiler and decides which programming language the code belongs to based on the extension of the file.

even then compiling with 'g++', the same problem lies.
```
$ g++ CG_LP2.cpp -lglut
/tmp/ccv5rHzr.o: In function `myinit()':
CG_LP2.cpp:(.text+0x683): undefined reference to `gluOrtho2D'
collect2: ld returned 1 exit status

```

---

### Post by Zugzwang on 2010-05-09
> **dev.konverje said:**
> g++ is just alias for gcc, gcc is the actual compiler and decides which programming language the code belongs to based on the extension of the file.

Yes and no. When using "gcc", while the compiler will know that it is C++, the linker (which is also invoked) will not necessarily automatically link to the stdc++ library. Search this forum for details. Also compare your error messages. The undefined symbols are in fact different.

Now to the solution of the problem. The function "gluOrtho2D" is defined in the OpenGL library and not the glut library, so you need to link against it as well. "g++ CG_LP2.cpp -lglut -lGL" works fine with your code at least on this computer.

---

### Post by dev.konverje on 2010-05-09
> **Zugzwang said:**
> The function "gluOrtho2D" is defined in the OpenGL library and not the glut library, so you need to link against it as well. "g++ CG_LP2.cpp -lglut -lGL" works fine with your code at least on this computer.

Nope that still doesn't solve it, i suppose it is something to do with shared libraries or such under lucid lynx (Ubuntu 10.04)

at the moment i am compiling under a 9.10 virtual machine and executing the generated executable under 10.04 and it is executing fine.

---

### Post by Zugzwang on 2010-05-09
Ok, then try linking against libGLU as well by adding "-lGLU" to your compiling/linking command. Note that the order of libraries is important, so try putting it before "-lglut", between "-lglut" and "-lGL", and after "-lGL".

---

