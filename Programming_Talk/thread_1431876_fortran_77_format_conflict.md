---
title: "fortran 77 format conflict"
date: 2010-03-17
forum: Programming Talk
---

### Post by valj on 2010-03-17
Hello there,

I made a f77 code from an old code someone gave me. My code is supposed to read a few columns and do some operations with those columns.

>       read(10,323)pres(i),hgt(i),temp(i),dwp(i),relh(i),mixr(i),drct(i)
     1,sknt(i),thta(i),thte(i),thtv(i)
323   format(f7.1,i7,2f7.1,i7,f7.2,2i7,3f7.1)
.
.
.
      zsnd(i)=float(hgt(i))
      thsnd(i)=thta(i)
      ang=float(drct(i))*pi/180.
      qvsnd(i)=float(relh(i))/100.
      usnd(i)=-sknt(i)*knot*sin(ang)
      vsnd(i)=-sknt(i)*knot*cos(ang)
 

When compiling (with gfortran), I get this error:

> 
sounding.f:23.20:

      zsnd(i)=float(hgt(i))                                             
                    1
Error: 'a' argument of 'float' intrinsic at (1) must be INTEGER
sounding.f:25.16:

      ang=float(drct(i))*pi/180.                                        
                1
Error: 'a' argument of 'float' intrinsic at (1) must be INTEGER
sounding.f:26.21:

      qvsnd(i)=float(relh(i))/100.                                      
                     1
Error: 'a' argument of 'float' intrinsic at (1) must be INTEGER


I can't understand the reason because I've checked many times and my input has the format f7.1,i7,2f7.1,i7,f7.2,2i7,3f7.1. Do you guys have any idea?

PS: I know the code is ugly and all, no implicit none, etc... but I didn't make the previous code which actually works pretty well.

---

### Post by lisati on 2010-03-17
I suspect that unless you have declared it otherwise, the mix variable might be being interpreted as integer.

From [http://www-classes.usc.edu/engr/ce/108/text/fbk01.htm](http://www-classes.usc.edu/engr/ce/108/text/fbk01.htm) :
> The basic Fortran types of integer and real single precision numbers do not have to be specified and there is a default which all Fortran programmers should memorize. All variable names which begins which the letters A-H and O-Z represent, by default, Single Precision Real Numbers. All variable names which begins with I, J, K, L, M and N represent, by default, Integers (whole numbers). All other types of variables have to defined at the beginning of the program module (main program or subprograms) using specification statements. There is no particular order for these specification statements, but they must appear before ANY executable statements. 

---

### Post by valj on 2010-03-17
Thank you,

I think it helped because I added some i- prefix or p- prefix and I don't get the error anymore but I have another error:

> 
sounding.f:3.72:

     1,isknt(n),thta(n),thte(n),thtv(n)                                 
                                                                        1
Error: Expected another dimension in array declaration at (1)
sounding.f:13.22:

      read(10,323)pres(i),ihgt(i),temp(i),dwp(i),irelh(i),pmixr(i),idrct
                      1
Error: Syntax error in READ statement at (1)


Here is the whole code:
> 
      PARAMETER(n=61,m=61)
      DIMENSION pres(n),ihgt(n),temp(n),dwp(n),irelh(n),pmixr(n),idrct(n)
     1,isknt(n),thta(n),thte(n),thtv(n)
      DIMENSION zsnd(n),thsnd(n),qvsnd(n),usnd(n),vsnd(n)

      open(unit=10,file='may11.snd',status='old')
      open(unit=11,file='may11.sndi',status='unknown')
      do 2 i=1,4
      read(10,321)info
 321  format(a1)
  2   continue
      do 16 i=1,n
      read(10,323)pres(i),ihgt(i),temp(i),dwp(i),irelh(i),pmixr(i),idrct(i)
     1,isknt(i),thta(i),thte(i),thtv(i)
323   format(f7.1,i7,2f7.1,i7,f7.2,2i7,3f7.1)
 16   continue

      pknot=0.514
      pi=acos(-1.)

      do 1 i=1,n

      zsnd(i)=float(ihgt(i))
      thsnd(i)=thta(i)
      ang=float(idrct(i))*pi/180.
      qvsnd(i)=float(irelh(i))/100.
      usnd(i)=-float(isknt(i))*pknot*sin(ang)
      vsnd(i)=-float(isknt(i))*pknot*cos(ang)    

1     continue      
     
      do 88 i=1,m
      write(11,67)zsnd(i),thsnd(i),qvsnd(i),usnd(i),vsnd(i)
67    format(5f13.5)
88    continue

      stop

      end 
    


---

### Post by valj on 2010-03-17
Ok, I finally decided to declare all the variables type and it worked.

---

