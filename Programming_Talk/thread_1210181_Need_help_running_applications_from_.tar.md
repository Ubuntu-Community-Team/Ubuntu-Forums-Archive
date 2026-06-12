---
title: "Need help running applications from .tar"
date: 2009-07-11
forum: Programming Talk
---

### Post by Jefferythewind on 2009-07-11
Hi Everyone, i have another possible super-simple question, but i haven't been able to find an answer:

How do i run a program that i installed from a .tar package?

i have had this problem a few times now.  Everything seems to go fine from the commands:

./configure
make
make install

But then i don't know how to start the program.

):P

---

### Post by fr4nko on 2009-07-11
You should guess or find the name of the executable to launch the program and simply type it from the console.

To find the name you can look around in the source files to spot the required file. An easy way can be to type:
> find my-source-directory -type f -a -executable
where my-source-directory is the directory where you extracted the files. This command search in the directory my-source-directory all the ordinary files that are executable.

Francesco

---

### Post by lavinog on 2009-07-11
Many times a README or INSTALL file can give this info.

---

