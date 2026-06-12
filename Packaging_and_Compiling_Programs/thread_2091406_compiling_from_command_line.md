---
title: "compiling from command line"
date: 2012-12-05
forum: Packaging and Compiling Programs
---

### Post by Stormey on 2012-12-05
Hi guys!
i'm new here and i have a question.

i've created three C program files - one source file, named "main.c", and two more called "functions.c" and "functions.h".

the first contains the main program, the other two are source (contains functions) and header files (contains function declarations);
i want to compile them from the command line.
what is the right command to do it?

thanks in advanced!

---

### Post by SeijiSensei on 2012-12-05
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Bachstelze on 2012-12-05
> **SeijiSensei said:**
> [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

That's not at all what OP is talking about...

Do

```
gcc -c main.c
gcc -c functions.c
gcc main.o functions.o
```

it will create your executable as a.out. Of course, add your favourite CFLAGS. ;)

---

### Post by Stormey on 2012-12-05
> **Bachstelze said:**
> That's not at all what OP is talking about...

Do

```
gcc -c main.c
gcc -c functions.c
gcc main.o functions.o
```it will create your executable as a.out. Of course, add your favourite CFLAGS. ;)

brilliant.
thanks!

---

