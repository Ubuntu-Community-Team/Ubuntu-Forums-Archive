---
title: "Making a process tree with fork() and FOR"
date: 2007-05-18
forum: Programming Talk
---

### Post by nnarayann on 2007-05-18
Edit: Sorry, Wrong post. Look at #3. Thx.

---

### Post by slavik on 2007-05-18
your children have to know where they are in a tree and maybe even have some config file or something ...

remember that memory references are kept after fork() (if you don't use assignment) this way you can tell who is who ...

---

### Post by nnarayann on 2007-05-18
First of all, thanks for answering.

I have new information about my problem. In fact, forget my previous post.

I need to create a function **void arbolN(int n)** that creates a tree of UNIX processes based on a parameter n (always an odd number). The number of children will be **(k+1)*(k+1)** where **n=2k +1**.

I.E. If n=7:

[IMG]http://img466.imageshack.us/img466/9509/arbollabssoonn4.jpg[/IMG]

I have no idea to resolve this cos I always have made forks sequentially (no loops).

Thx.

---

### Post by slavik on 2007-05-20
I find your diagram confusing ... remember, when fork() is done, you have the original process running (return value is pid of child) and a child process (return value of 0).

also, in the end, do you want a total of n processes? or n to be the total number of processes?

---

### Post by nnarayann on 2007-05-20
First of all, thx again slavik.

I always put forks into a switch in order to have controlled them easily:

switch (fork()
{
    case -1 //ERROR
    case 0 //Child
    default //Parent
}

The total number of processes is calculated by (k+1)*(k+1) where n=2k +1. If n=7, the total number of processes is 16.

My problem, mainly, is to create the parent process because I think I have to call this function recursively (changing n value I supose). 

I have no idea to continue it, I have passed a few hours with it but... :(

Any idea??

---

### Post by slavik on 2007-05-20
num of procs = (((n-1)/2)+1)^2 (no need for k :D)

n = 1, num = 1
n = 3, num = 4
n = 5, num = 9
n = 7, num = 16
n = 9, num = 25

there's lots of checking that needs to happen ... basically, calculate the total number of processes you will have, then take closest power of 2 and fork until the next fork put you over the number and have the parent fork the rest.

hint: save the parent pid in the very beginning of the program.

---

### Post by nnarayann on 2007-05-20
Thanks slavik, now I´m on the right way :D. Tomorrow morning I´ll finish it for sure.

Regards, nnarayann.

---

