---
title: "Compiling code with gcc"
date: 2006-10-09
forum: Programming Talk
---

### Post by mavix on 2006-10-09
How do I complile a .c source file in gcc? I went into the terminal and typed(I was in the desktop dir):gcc test.c
It then produced a file called a.out. What must I do now?

---

### Post by SoggyCornflake on 2006-10-09
a.out is the program, but it probably isn't executable yet.  

You need to change it't permissions by typing
[INDENT]
**chmod +x a.out**[/INDENT]

Now to run it type 

[INDENT]**./a.out**[/INDENT]

---

### Post by mavix on 2006-10-09
Thanks

---

### Post by amo-ej1 on 2006-10-09
the a.out as a result by gcc is made executable by default so you wouldn't need to do the chroot. You might want to consider


```

gcc -o output_name source.c

```
that will create a binary called 'output_name' instead of a.out.

---

