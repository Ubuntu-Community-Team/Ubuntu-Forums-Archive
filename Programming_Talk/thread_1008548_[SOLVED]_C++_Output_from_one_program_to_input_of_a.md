---
title: "[SOLVED] C++ Output from one program to input of another"
date: 2008-12-11
forum: Programming Talk
---

### Post by kjohansen on 2008-12-11
I know this is a simple task that can be done but I cant think of the right words to put into google to get a result.

I want to have:

./prog1.o > ./prog2.out

so what is written on stdout of prog1 is passed to prog2 as input.  How do I access this input in C++?

prog1 does some data transformations that I want to keep out of prog2 and not be forced to write to file and have prog2 read the file.

thanks.

---

### Post by Simian Man on 2008-12-11
This is called piping and is achieved like so:

./prog1 | ./prog2

Your programs don't need to do anything extra to make this work.  prog1 writes to stdout and prog2 reads from stdin.

HTH

---

