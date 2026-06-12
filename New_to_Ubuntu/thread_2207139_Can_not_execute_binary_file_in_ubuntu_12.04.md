---
title: "Can not execute binary file in ubuntu 12.04"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by assaf2 on 2014-02-22
Hello everyone,

I am a new user at ubuntu and I'm programming c in that platform.

Now I tried two ways to work, on the simple document writer and in Eclipse.

I both ways when I try to run a program on the terminal I get the following message:
```
bash: ./myprog: cannot execute binary file

```
Where myprog is a compiled c program with this code:
```
gcc -ansi -Wall -c first.c -o myprog



```
My system is windows 8.1 with 64bit. 
Please note that I have had a 64bit OS on my previous laptop and I managed to run files in that ubuntu system with no problems, so I don't think it's a 64-bit 32-bit kind of problem.
It doesn't matter if I write the code on eclipse or in the document writer, everytime I try to run my file I get the same error.

Please, your help is highly appriciated, thank you!

---

### Post by Impavidus on 2014-02-22
So, do you use Windows 8 or Ubuntu 12.04? Programs compiled on Windows won't run on Ubuntu, and vice versa. Running your programs in Ubuntu from a Windows partition won't work either, but that gives you a "permission denied" error, instead of the "cannot execute binary file" error.

---

### Post by assaf2 on 2014-02-22
Oh I am sorry for not clearing this out - I am running ubuntu 12.04 on VMWARE as a terminal on windows 8.1 64 BIT.

---

### Post by steeldriver on 2014-02-22
Drop the -c flag - it stops compilation short (at the object file stage) rather than linking with the standard libraries necessary to create an actual executable

```
gcc -ansi -Wall first.c -o myprog
```

From **man gcc**
```

       -c  Compile or assemble the source files, but do not link.  The linking
           stage simply is not done.  The ultimate output is in the form of an
           object file for each source file.

```

---

### Post by Impavidus on 2014-02-22
Good catch, I missed the -c option. That must be it.

---

