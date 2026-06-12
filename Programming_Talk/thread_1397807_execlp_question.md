---
title: "execlp question"
date: 2010-02-03
forum: Programming Talk
---

### Post by madpig on 2010-02-03
I was wandering, why when I use a execlp function I have to add NULL as last argument?
execlp(arg1, arg2, ..., NULL)
Could anyone help me to understand? I searched all over the web but cannot find anything useful.
THX

---

### Post by denarced on 2010-02-03
That's funny.
I guess the function's just built that way but I can't figure out why.

---

### Post by lisati on 2010-02-03
This is just a guess (someone can correct me if I'm mistaken), but some functions can accept multiple arguments. Having NULL as the last one is a way of telling the called function when to stop checking for arguments.

---

### Post by Brandon Williams on 2010-02-04
The exec family of functions always takes a NULL terminated array of arguments. You can either specify it as a vector (e.g. execvp) or a list (e.g. execlp). In both cases, there is no way to tell the system how many elements there are in the array, so NULL termination is simply a way to mark the end of the array. The NULL serves the same purpose as the '\0' at the end of a C-string. Also, requiring the NULL array termination makes the input to exec look the same as the argv array that the program being executed will receive.

---

### Post by madpig on 2010-02-04
I thought there is some another way to count arguments. Thanks for help.

---

