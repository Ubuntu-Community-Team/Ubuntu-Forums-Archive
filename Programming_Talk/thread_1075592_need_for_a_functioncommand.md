---
title: "need for a function/command"
date: 2009-02-20
forum: Programming Talk
---

### Post by veda87 on 2009-02-20
I am doing a program in which i have to get some numbers(say 1, 2, 3, 4, 5). all i need to do is to get its sum(15). i am giving the input through "echo -n 1 2 3 4 5 > /dev/veda ". i get these inputs through **copy_from_user**. it is in char * but i have to change into integers so that i could sum them. Is there is any function/command for changing **char into a integer**.(similar to **atoi** in C programming).

then i have to change the **integer into char** so that i can print it through **copy_to_user** function. so i need a function/command for this also.(similar to **itoa** in C programming).

can anyone know the function/command for doing this.....

---

### Post by monkeyking on 2009-02-20
Are you talking about shell programming?
Or what language are you using

check out dc and bc if you're using it from the shell

---

### Post by veda87 on 2009-02-20
i am doing this read/ write operation for a driver module program. so i am using linux kernel functions. so i need a kernel function for performing those operations.

---

### Post by jpkotta on 2009-02-20
Use the kernel's version of strtol().

[http://fxr.watson.org/fxr/ident?v=linux-2.6;i=simple_strtol](http://fxr.watson.org/fxr/ident?v=linux-2.6;i=simple_strtol)

---

### Post by veda87 on 2009-02-22
i got simple_strtol for changing a string into an integer but now i need a function for converting **integer to char** (similar to **itoa** function in c) so that i can print the integer through copy_to_user.

can anyone tell me that kernel function.

---

### Post by jpkotta on 2009-02-23
Same as for userspace: snprintf().

---

