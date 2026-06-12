---
title: "No targets specified and no makefile found"
date: 2011-12-20
forum: Programming Talk
---

### Post by das86 on 2011-12-20
Hi, 
I am using Kate to compile  a small project, but it keeps giving me the error : No targets specified and no makefile found.
Any ideas?

---

### Post by Zugzwang on 2011-12-20
Kate appears to assume that you put a "Makefile" into the directory of your project. See [Here]("http://wlug.org.nz/MakefileHowto") for some details and examples. Also, visit [wikipedia]("http://en.wikipedia.org/wiki/Makefile") for a quite good description of the overall make process.

---

### Post by das86 on 2011-12-21
I did create a makefile in the directory.
sandbox: sandbox.o
  ld -o sandbox sandbox.o
sandbox.o:sandbox.asm
  nasm -f elf -g -F stabs sandbox.asm

but it keeps giving me the same error. I am using Jeff Duntemann's book btw. Great book, but this error is really making me slow in my study!!!

---

### Post by Zugzwang on 2011-12-21
Watch the capitalization: the file must be named "Makefile" and not "makefile". Then, check if kate is executing the "make" command in the correct directory.

---

### Post by Arndt on 2011-12-21
> **Zugzwang said:**
> Watch the capitalization: the file must be named "Makefile" and not "makefile". Then, check if kate is executing the "make" command in the correct directory.

Actually, 'make' should look for "makefile" as well as "Makefile", but I don't what this Kate thing is expecting.

---

### Post by Zugzwang on 2011-12-22
> **Arndt said:**
> Actually, 'make' should look for "makefile" as well as "Makefile", but I don't what this Kate thing is expecting.

I would say that it is: "make: *** No targets specified and no makefile found.  Stop" is precisely what the make tool reports when not finding a makefile, and this is letter-by-letter the original error message by the OP (modula stuff that he/she removed). Also, kate is only an editor and thus, hitting "compile" in any form shouldn't trigger something complicated.

---

### Post by das86 on 2011-12-24
The error was because I had been saving it as makefile.asm
beginner stupid error:D

---

