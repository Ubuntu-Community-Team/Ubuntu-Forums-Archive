---
title: "Fortran"
date: 2006-05-09
forum: Programming Talk
---

### Post by aam-aadmi on 2006-05-09
I have installed Ubuntu on my system about a month ago and am relatively comfortable with the new OS. Now, I want to do some computing (estimating models using maximum likelihhod estimation) in Fortran. Any suggestions or guidelines on getting started is welcome. I have some previous experience with Pascal (but that is about a decade ago). Also: does anyone know of libraries of Fortran code (like maximizing functions and solving linear equation systems)?

---

### Post by drl on 2006-05-10
Hi, aam-aadmi.

There is a *lot* of information at [http://www.fortran.com/](http://www.fortran.com/), including libraries, books, etc., some commercial, some free.  After you look that over, let us know more specifically what you might need, or might be looking for.  

For example, what compiler do you intend to use? ... cheers, drl

---

### Post by aam-aadmi on 2006-05-10
Thanks a lot. I will probably use the Fortran 95 compiler.

---

### Post by aam-aadmi on 2006-05-11
I have some very basic questions:

1) I have installed gfortran using the synaptic package manager; now, how do I read the documentation that comes along with this compiler?

2) I wrote a small test program using Gedit and saved it without any extension. Then I tried compiling the program using the following command:
        gfortran filename
I get an error message saying: gfortranc: command not found
Am I making some stupid mistake? Should I save the program file with some specific extension? Should I invoke the fortran comiler with some other command?

Any help will be greatly appreciated.

Thanks in advance.

---

### Post by drl on 2006-05-11
Hi, aam-aadmi.

1) man gfortran

2) use ".f" to start with, so you would run it as:
```

gfortran filename.f
```
In the man page, you will see that there are other extensions ... cheers, drl

---

### Post by Hoffmann on 2006-05-11
[QUOTE=aam-aadmi]I have some very basic questions:

1) I have installed gfortran using the synaptic package manager; now, how do I read the documentation that comes along with this compiler?

2) I wrote a small test program using Gedit and saved it without any extension. Then I tried compiling the program using the following command:
        gfortran filename
I get an error message saying: gfortranc: command not found
Am I making some stupid mistake? Should I save the program file with some specific extension? Should I invoke the fortran comiler with some other command?

Any help will be greatly appreciated.

Thanks in advance.[/QUOTE]


Since you are interested in the last stable version of Fortran (Fortran 95), you should use the .f90 extention in all of your codes.
In order to compile with gfortran:

```

gfortran -o filename filename.f90
```

This way you will generate the executable filename (from the filename.f90 file).

---

### Post by Hoffmann on 2006-05-11
[QUOTE=aam-aadmi]I have installed Ubuntu on my system about a month ago and am relatively comfortable with the new OS. Now, I want to do some computing (estimating models using maximum likelihhod estimation) in Fortran. Any suggestions or guidelines on getting started is welcome. I have some previous experience with Pascal (but that is about a decade ago). Also: does anyone know of libraries of Fortran code (like maximizing functions and solving linear equation systems)?[/QUOTE]

Also a nice alternative is the Intel Fortran Compiler for Linux: 

[http://www.intel.com/cd/software/products/asmo-na/eng/compilers/282048.htm](http://www.intel.com/cd/software/products/asmo-na/eng/compilers/282048.htm)

This program is free for personal use.

---

### Post by aam-aadmi on 2006-05-11
Thanks a lot for all your suggestions. I will compile my first fortran program shortly and I am damn excited!

---

### Post by Lux Perpetua on 2006-05-13
See also:

[http://netlib.org](http://netlib.org)

for tools and libraries. You can find various numerical analysis packages there, including Fortran numerical linear algebra packages.

---

