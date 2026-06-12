---
title: "Running Fortran programs"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by GeoffreyBernardo on 2008-09-22
Hallo there,

I have installed the intel fortran compiler and I am trying to run my first program. I write the program (e.g. test) in gedit and save it in the **home/[username]** directory as **test.f90**. Then I compile it in the command line with **ifort test.f90**. The a.out file is created. Then when I type in test in the command line, I get the error **command not found**.

Please help.

---

### Post by aeiah on 2008-09-22
i havent messed with fortran, but at a guess, if the compiler spat out a.out, that is your compiled program. in that case, you would want to, whilst in the directory that your program resides, do:

```

./a.out
```

the reason for the ./ is because the program is not in your path, and you need to specify that you're executing the file that's located in your working directory.

---

### Post by GeoffreyBernardo on 2008-09-22
> **aeiah said:**
> i havent messed with fortran, but at a guess, if the compiler spat out a.out, that is your compiled program. in that case, you would want to, whilst in the directory that your program resides, do:

```

./a.out
```

the reason for the ./ is because the program is not in your path, and you need to specify that you're executing the file that's located in your working directory.

Thanks very much! That works splendidly.

---

### Post by GeoffreyBernardo on 2008-09-22
How do I compile a file that is in a directory other than the home/[username] directory?

For example, I have a file ch0701.f90 in the **/home/geoffrey/Documents/Fortran Computer Programming directory.**

---

### Post by GeoffreyBernardo on 2008-09-22
> **GeoffreyBernardo said:**
> How do I compile a file that is in a directory other than the home/[username] directory?

For example, I have a file ch0701.f90 in the **/home/geoffrey/Documents/Fortran Computer Programming directory.**

Nevermind. I got it.

ifort ./Documents/Fortran\ Computer \Programming/ch0701.f90

:)

---

