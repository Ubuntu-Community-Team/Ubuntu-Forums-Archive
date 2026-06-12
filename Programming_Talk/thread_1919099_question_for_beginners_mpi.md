---
title: "question for beginners mpi"
date: 2012-02-02
forum: Programming Talk
---

### Post by corthom on 2012-02-02
Hi everybody.

I'm trying to learn a bit mpi. But I've got a question. I use fortran90.

If I declare a variable in the beginning of the program, as far as I've understood, every process will have an own "copy" of that variable. I mean if I have a variable "a" and I say write(*,*) a, every process will print its own variable "a".

Is it possible to declare a variable such that only a particular process knows about it? for example such that if I write something like 

if (rank==1) write(*,*) a

is ok, but

if (rank==0) write(*,*) a

gives an error?

This would be useful, I think, in order not to waste memory, in some cases... I couldn't find an answer to this question. Thanks in advance

                     Thom

---

