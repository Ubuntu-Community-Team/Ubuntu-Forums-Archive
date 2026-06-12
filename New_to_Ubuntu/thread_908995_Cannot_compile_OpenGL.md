---
title: "Cannot compile OpenGL"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by jwilley44 on 2008-09-03
Hello

I am trying to compile a C program which uses OpenGL. The header that is used is
#inlcude <GL/glut.h>
I have looked in usr/GL and it is in there along with other .h files. The errors that I receive are of the form 'undefined reference to glutSetColor'
I also tried using a MAKEFILE but I am not sure what to set GL equal to (I am not very savy with a MAKEFILE). If this does not make sense then just some command line compiling commands would also be extremely helpful.

Thanks in advance.

---

### Post by Perfect Storm on 2008-09-03
Have you installed glut development package from the repo? (something similiar to libglut-dev, not on my ubuntu machine to check this)

---

### Post by jwilley44 on 2008-09-03
So I just installed libglut-dev from the synaptic package manager, but no luck (same error messages). What libraries should I link to when compiling?

---

### Post by Perfect Storm on 2008-09-03
Can you attach in/out-put from start to finish.

---

### Post by jwilley44 on 2008-09-03
Not sure what that means.

---

### Post by howlingmadhowie on 2008-09-03
> **jwilley44 said:**
> So I just installed libglut-dev from the synaptic package manager, but no luck (same error messages). What libraries should I link to when compiling?

something like this may well work: 

```
gcc simple.c -o simple -I/usr/X11R6/include/ -L/usr/X11R6/lib -lX11 -lXi -lXmu -lglut -lGL -lGLU
```

---

### Post by Perfect Storm on 2008-09-03
what you type in the terminal and what it spits out.

---

### Post by jwilley44 on 2008-09-03
So in my Makefile I GL = -lglut and that got rid of the errors. There are some other things wrong but I think that is probably just the code I downloaded. Thanks.

---

