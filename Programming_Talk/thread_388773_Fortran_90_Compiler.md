---
title: "Fortran 90 Compiler"
date: 2007-03-19
forum: Programming Talk
---

### Post by nonpareilpearl on 2007-03-19
Hello ^.^

I recently asked a professor if he would be interested in having an undergrad assist with anything, and he said an nice undergrad project would be to edit the compiler flags and etc. of a certain program (to increase speed and efficiency). While poking around to see if there were any Fortran 90 compilers for Ubuntu, I did come across [this]("http://packages.ubuntu.com/dapper/virtual/fortran-compiler"), however I am relatively new to this process. Will either of these work with Fortran 90 code? Is there a Fortran 90 compiler for Ubunu?

Some things I will need to learn: How to manipulate the "makefile", Fortran basics (I have learned C before, so this isn't proving to be too awful but a decent link to a guide is always welcome), and any other info appreciated.

Thanks :D

---

### Post by WW on 2007-03-19
Yes, gfortran will work with Fortran-90.

---

### Post by xadder on 2007-03-20
My favourite `small' Fortran-95 is F, which is also easy to install. F is Fortran'95 but without 90% of the historical stuff which still forces compilers to deal with Fortran IV constructs. (i.e. all F programmes are very strict fortran-95 programs, but not vice-versa). See [www.fortran.com](www.fortran.com) for more Info on this nice program.

Otherwise g95 is also easy to install (and provides F through compiler flags if wanted!), and free. I like to have F, gfortran and g95 handy - all compilers give different warnings, so this is a great help. 

Intel also provide a very good and fast fortran compiler, ifort, which is free for non-commercial use. Faster than gfortran or g95, but of course a license is needed and expensive for commercial use.

---

### Post by sfp100 on 2010-05-25
Hi, guys
I have a similar problem, but I need Fortran90 exactly. I try use 
```
 
REAL :: t, dt, tmax
[...]
DO t=0,tmax,dt 

```and gfortran sed:
```

DO t=0,tmax,dt
   1
Warning: Deleted feature: Loop variable at (1) must be integer

```while this correct (obsolescent but should work) according to J.C.Adams et al. "Fortran 90 Handbook. Complete ANSI/ISO Reference". I thing that in pure Fortran 90 this should work, but gfortran known dialects: ‘f95’, ‘f2003’, ‘gnu’, or ‘legacy’. 
Have you know any other way to do this, better than
```
 
INTEGER :: i,maxiter
maxiter = tmax/dt
DO i=0,maxiter,1

```?

---

### Post by gonza85 on 2010-09-05
have you consider using 'do while' instead of 'do'??

try this:

```

real(8):: t, tmax, dt

t=0
do while(t<=tmax)
     .
     .
     .
     .
     t=t+dt
end do

```let me know if it worked! ;)

---

### Post by pallukucchu on 2010-09-06
Dear all,
         I want to write an array A(1:64) containing 64 elements to a text file in a single row. Can anyone suggest a trick to do this in Fortran 90?

Thanking you,
Pallukucchu.

---

### Post by sfp100 on 2010-09-08
@[gonza85]("http://ubuntuforums.org/member.php?u=1143540"): thanks for answer. I think it is what I had been looking for, but I've closed this project some weeks ago, even I can't remember how I've solved this problem :-(
Any way, thanks. 

@pallukucchu:
If this has one dimension it should be simple. You can try
```
open(22,file="nazwa_pliku", status="new")
write(22,888) A
888 format(64G12.5,1X)

```format(...) gives definition of output format and there is: 64 times do:
G - scientific notation
12.5 - 12 digits, in this number 5 digits after dot ('.')
1X - one tabulation between digits.

Other formats you can find in fortran documentation (for example in book I've mentioned above, but  this one is quite large and hard for beginers like me).

If 
```
write(22,888) A
```didn't give you expect to, try
[HTML]write(22,888) (A(i), i=1,64)[/HTML]I'm quite sure that if you wait some time any more competent answer you should receive.

---

