---
title: "compile problems in gfortran"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by dog6 on 2008-07-08
This is the program I was using in pico and saved as hello_world.f9

GNU nano 2.0.7 File:hello_world.f9 

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

### Post by ZabiGG on 2008-07-09
Hi there ;)

I know nothing about fortran, but logically it's indicating that it's bugging on your "implicit" line. Is there any symbol or code missing there? Also, other languages require an exit code. I don't see any exit code (like exit 0, 0 or anything) telling the program to end... But then, I did say I knew nothing about fortran.

---

### Post by sdennie on 2008-07-09
Looks like you forgot to indent your statements.  I think you need like 6 or 8 spaces before statements can appear.

---

### Post by systemdamage on 2008-09-05
Your code seems ok, but it is written on version 90,95 of FORTRAN. Then, you need to rename your file to FILENAME.f90 (notice the f90 as file extension).

If you don't do that, gfortran will threat your file as a FORTRAN 77 code, and FORTRAN 77 works a little bit different from the FORTRAN 90 (or 95, which you written your file).

I think that may help!

Sorry my bad english!

Regards!:guitar:

---

### Post by abalter on 2009-08-22
I'm having the same issue.  I'll try the solution and see if it works.

---

### Post by abalter on 2009-08-22
Tried it.  Still getting error, but  different error:
unidentified reference to 'MAIN__'

---

### Post by abalter on 2009-08-25
abalter@scibox:~/Fortran$ cp foo.f foo.f95
abalter@scibox:~/Fortran$ gfortran foo.95
gfortran: foo.95: No such file or directory
abalter@scibox:~/Fortran$ gfortran foo.f95
/usr/lib/gcc/i486-linux-gnu/4.3.3/libgfortranbegin.a(fmain.o): In function `main':
(.text+0x35): undefined reference to `MAIN__'
collect2: ld returned 1 exit status
abalter@scibox:~/Fortran$ which f95
/usr/bin/f95
abalter@scibox:~/Fortran$ f95 foo.f95
/usr/lib/gcc/i486-linux-gnu/4.3.3/libgfortranbegin.a(fmain.o): In function `main':
(.text+0x35): undefined reference to `MAIN__'
collect2: ld returned 1 exit status
abalter@scibox:~/Fortran$ f95 foo.f90
/usr/lib/gcc/i486-linux-gnu/4.3.3/libgfortranbegin.a(fmain.o): In function `main':
(.text+0x35): undefined reference to `MAIN__'
collect2: ld returned 1 exit status
abalter@scibox:~/Fortran$

---

### Post by cholericfun on 2009-09-18
use compiler options - 
in gfortran it is -ffree-form
in ifort it is -FR

this way youre not too restricted.

---

### Post by sfp100 on 2010-05-25
[abalter]("http://ubuntuforums.org/member.php?u=39294"), could you post program code and compilation line? I can't understand listening you paste in last post.
It should help us to help you :P

---

### Post by spb on 2011-09-27
I'm very curious if this has been solved.  I'm encountering a very similar issue.  

I'm guessing that this is a very simple problem, but I'm not able to guess the solution from the error message:

/usr/lib/gcc/x86_64-linux-gnu/4.4.3/32/libgfortranbegin.a(fmain.o): In function `main':
(.text+0x27): undefined reference to `MAIN__'
collect2: ld returned 1 exit status

Thanks,
S

---

### Post by oldos2er on 2011-09-27
Closed for necromancy. Please start a new thread.

---

