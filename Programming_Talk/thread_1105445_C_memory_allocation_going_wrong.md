---
title: "C memory allocation going wrong"
date: 2009-03-24
forum: Programming Talk
---

### Post by spudgunner on 2009-03-24
I'm doing a project for school where a partner and I have been required to develop a very basic file system. We are just about done it, only one function left to test (everything else has been tested seperate and together), and we're having a big problem involving memory.

We have to keep track of some structs (four at a time, to be exact), and one of the peices of these structs is a char pointer. For some reason, we load one into the program as needed (allocating memory for the char pointer), however, when we try to load another or allocate memory for something else, the allocation seems to overright hte first file's allocation (the values the char pointer points to are changed). For your reference, there is main function calling other functions we wrote, and these functions are what is allocating the memory (unless we allocate in the main function for testing purposes). There are no errors or warnings during compilation, and nothing crashes during execution.

Any idea of why this is happening, and how we can fix it?

Thanks,

Josh

---

### Post by dwhitney67 on 2009-03-24
Um, did you have any plans to post your code so that we can review it for errors?  Remember, we are not psychic!

---

### Post by monkeyking on 2009-03-24
Try using gdb and valgrind,

These tools are excellent for this.

Good luck

---

### Post by spudgunner on 2009-03-24
Turns out I made a typo, my parnter just caught it... nevermind, but thanks for your offerings of help and suggestions.

---

