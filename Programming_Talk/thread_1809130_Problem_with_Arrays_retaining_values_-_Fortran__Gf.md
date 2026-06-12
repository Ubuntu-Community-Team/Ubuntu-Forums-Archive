---
title: "Problem with Arrays retaining values - Fortran / Gfortran"
date: 2011-07-21
forum: Programming Talk
---

### Post by jflock on 2011-07-21
I am a physics postgrad, and have a program that I use for data analysis that is written in Fortran. I have modified an existing code to add extra functions.

However I am having problems with variables and arrays retaining values. These variables and arrays are all declared in a file common.f as global variables like so:

        REAL*8 DTRA,DLTA2,DTRF
        COMMON/DTRA1/DTRA,DLTA2,DTRF

There are many other such common blocks. 

I have managed to fix the problem of a number of variables not retaining their values by changing their position in common blocks / changing which common block they were actually in, however one fairly vital 2 dimensional array still causes problems. Data is read into this array in one subroutine, then printed out immediately to check that is correct. This is fine. Then the next time that the array is used in a subsequent subroutine, and the contents have changed. I can work around this by hardcoding the data directly into the subroutine, but this is not a desirable long term solution, and I would like to know why this is not working.

I have extensively searched for a solution with no success. I am not a programmer as you can probably tell, and just want this to work so that I can get on with my research. If anyone can offer any help or advice at all I would be very grateful.

---

