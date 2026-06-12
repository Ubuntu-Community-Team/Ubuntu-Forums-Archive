---
title: "Fortran 77 error &quot;read start: end of file&quot;"
date: 2009-12-03
forum: Programming Talk
---

### Post by rachelb on 2009-12-03
I am completely new to Fortran and am getting the following error
"vislab01:~/fortran> ./mean_testb
 i=  1j =  1  2.33999991
 i=  1j =  2  1.01999998
 i=  1j =  3  0.560000002
 i=  2j =  1  3.91000009
read start: end of file
apparent state: unit 1 named polar.dat
last format: list io
lately reading direct formatted external IO
Abort"

I can compile. but when I run it I get this message.  It doesn't want to read all the data file.  Here is my code:

    program mean_testb
c
    implicit none
c
c * Declare variables
    real  A(4,3) 
    integer i,j
c
c * Open files to read and write to
    open(1,file='polar.dat')
c
c * Read the first row of data and find average
    do i=1,4
       do j=1,3
          read(1,*)A(i,j)
          write(*,*)'i= ',i,'j = ',j,A(i,j)
       enddo
    enddo
c
    close(1)
c    
    end

Is it a really obvious mistake?  Sorry, but have only been at this a couple of days and will need to get a lot better!!  Rachel

---

