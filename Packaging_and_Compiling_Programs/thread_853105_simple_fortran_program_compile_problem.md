---
title: "simple fortran program compile problem"
date: 2008-07-08
forum: Packaging and Compiling Programs
---

### Post by dog6 on 2008-07-08
I am a first time programmer and have had difficulties getting this simple program to compile, any questions...?
--------------------------------------------------------------------------------

This is the program I was using in pico and saved as hello_world.f

GNU nano 2.0.7 File:hello_world.f 

Program Hello_World
implicit none
Print *, "Hello, world!"
End Program Hello_World


*** The text below is what happened when I tried to compile... any suggestions..?

jerome@jerome-laptop:~$ gfortran -c hello_world.f
hello_world.f:1.1:

Program Hello_World 
1
Error: Non-numeric character in statement label at (1)
hello_world.f:1.1:

Program Hello_World 
1
Error: Unclassifiable statement at (1)
hello_world.f:4.1:

End Program Hello_World 
1
Error: Non-numeric character in statement label at (1)
hello_world.f:4.1:

End Program Hello_World 
1
Error: Unclassifiable statement at (1)
Error: Unexpected end of file in 'hello_world.f'

---

### Post by WW on 2008-07-08
Change the name of your file to hello_world.f90.

See the section "Controlling the input source form" [here](http://gcc.gnu.org/wiki/GFortranUsage).


P.S. You say you are a first time programmer.  Do you have a compelling reason to use Fortran as your first language?

---

### Post by dog6 on 2008-07-08
I will try that, another friend recommended that i try starting the program in column 7 instead of columns 1 thru 5...?

I have just started with a professor that likes to write algorithms in fortran code for use in seismic processing / attributes in the geophysics field...

---

### Post by WW on 2008-07-08
> **dog6 said:**
> I will try that, another friend recommended that i try starting the program in column 7 instead of columns 1 thru 5...?

I have just started with a professor that likes to write algorithms in fortran code for use in seismic processing / attributes in the geophysics field...
OK, but you should find out *which* Fortran your professor uses: Fortran 77 or Fortran 90.  Your "Hello, world" program is Fortran 90.

---

### Post by djmac on 2009-08-10
Starting my program from column 7 solved my problems . . . . don't know why but it worked.

---

### Post by ianc on 2009-08-10
> **djmac said:**
> Starting my program from column 7 solved my problems . . . . don't know why but it worked.

From what I can remember from back in the days of yore the first 6 columns were reserved for line counters & a line continuation flag.

Mind you I haven't programmed in Fortran for >20 years...

---

### Post by sirgdjacobs on 2010-04-30
GFORTRAN guesses the source code formatting based on the file extension. For .f90 files, it will assume it's working with FORTRAN 90 source code and use free formatting rules. For .f and .for files, it will assume the file is F77 source code and use fixed formatting rules. I believe this is the problem you're experiencing.

```

odin@ibos:~$ cat test.f90
Program Hello_World
implicit none
Print *, "Hello, world!"
End Program Hello_World

odin@ibos:~$ cp test.f90 test.f

odin@ibos:~$ gfortran -o test test.f90

odin@ibos:~$ ./test
 Hello, world!

odin@ibos:~$ gfortran -o test test.f
test.f:1.1:

Program Hello_World                                                     
 1
Error: Non-numeric character in statement label at (1)
test.f:1.1:

Program Hello_World                                                     
 1
Error: Unclassifiable statement at (1)
test.f:2.1:

implicit none                                                           
 1
Error: Non-numeric character in statement label at (1)
test.f:2.1:

implicit none                                                           
 1
Error: Unclassifiable statement at (1)
test.f:3.1:

Print *, "Hello, world!"                                                
 1
Error: Non-numeric character in statement label at (1)
test.f:3.1:

Print *, "Hello, world!"                                                
 1
Error: Unclassifiable statement at (1)
test.f:4.1:

End Program Hello_World                                                 
 1
Error: Non-numeric character in statement label at (1)
test.f:4.1:

End Program Hello_World                                                 
 1
Error: Unclassifiable statement at (1)

```You can override the defaults with -ffixed-form and -ffree-form.

---

