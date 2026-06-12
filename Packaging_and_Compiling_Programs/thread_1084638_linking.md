---
title: "linking"
date: 2009-03-02
forum: Packaging and Compiling Programs
---

### Post by gian748 on 2009-03-02
Hi guys,

I have to "translate" some program written in BORLANDC for windows to C for linux.

The problem is that libraries like conio.h, stdio.h dos.h are not found in the gcc compiler that I have installed.

I have tried to copy the old ones form another pc (with windows) but the do not works even if the compliler find them. It says that they are full of errors.

The question is: With which libraries could I replace the old ones common in BORLANDC , like conio.h , dos.h and similars?

:confused:

many thanks

gian

---

### Post by chrisccoulson on 2009-03-03
stdio.h is part of libc6-dev, so you need to install these headers before compiling your application.

Both conio.h and dos.h are compiler/platform specific headers, so you should remove functions that rely on these (or use alternatives) when porting the application. I'm not sure what functions you use, and without that, it is difficult to suggest alternatives.

---

### Post by gian748 on 2009-03-03
could you suggest an help where I can find the functions that are present in GCC natural libraries???? something like a list of libraries and for each of them a list of fuctions that they contain....

many thanks

---

