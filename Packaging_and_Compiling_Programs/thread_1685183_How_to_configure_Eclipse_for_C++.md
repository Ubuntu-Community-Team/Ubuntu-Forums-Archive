---
title: "How to configure Eclipse for C++ ?"
date: 2011-02-10
forum: Packaging and Compiling Programs
---

### Post by jimmys_ on 2011-02-10
Hi. I need to configure Eclipse to develop C++. I have downloaded Eclipse and installed the C++ add-on. I'm trying to import an existing file with a makefile into Eclipse. I don't know if I'm doing it correctly but when trying to compile it I get the error: Launch failed. Binary not found. What's wrong?

---

### Post by Simian Man on 2011-02-10
Because Eclipse is just calling your makefile, it has no way of knowing what binary is the result of the compilation process.  You need to tell it yourself.  Go to "Run->Run Configurations", then you can enter the executable under the "Main" tab in the blank labeled "C/C++ Application".

HTH.

---

### Post by jimmys_ on 2011-02-10
Which file do I choose? There is no executable file. There is also an error in Eclipse:
make: *** No rule to make target `all'

---

