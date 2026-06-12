---
title: "how to execute GFORTRAN 95 program in ubuntu??"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by nsakib520 on 2012-11-27
Hi

I am very new to ubuntu and trying to execute a program in GNU FORTRAN 95 Compiler. I am able to compile and run a .f file (SPHYSICSgen_2D.f). But i cannot execute the program.

inside the terminal after going to the desired directory (SPHYICSgen2D) i did the following steps to create a program called new2 from the source code SPHYSICSgen_2D.f:

gfortran -o new2 SPHYSICSgen_2D.f

it created a new2 file. then to execute the new2 program i wrote:

./new2

bt it says permission denied as:

bash: ./new2: Permission denied


i also tried by logging in as a root.

How to solve this; please help me ...............


SAKIB

---

### Post by lykwydchykyn on 2012-11-27
Not a fortran expert, but try:
```

chmod +x new2

```

That will give execute permissions to the binary.  Probably they are not given by default, for security reasons or because of directory settings.

---

