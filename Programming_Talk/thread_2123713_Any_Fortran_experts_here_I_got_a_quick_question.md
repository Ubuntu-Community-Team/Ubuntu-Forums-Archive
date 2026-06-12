---
title: "Any Fortran experts here? I got a quick question"
date: 2013-03-08
forum: Programming Talk
---

### Post by PC_load_letter on 2013-03-08
Today is my first day to learn Fortran, I look for code samples and I stumble upon this one for the calculation of the area of a closed cylinder, here:
```
program cylinder
 
! Calculate the surface area of a cylinder.
!
! Declare variables and constants.
! constants=pi
! variables=radius squared and height
 
  implicit none    ! Require all variables to be explicitly declared
 
  integer :: ierr
  character(1) :: yn
  real :: radius, height, area
  real, parameter :: pi = 3.141592653589793
 
  interactive_loop: do
 
!   Prompt the user for radius and height
!   and read them.
 
    write (*,*) 'Enter radius and height.'
    read (*,*,iostat=ierr) radius,height
 
!   If radius and height could not be read from input,
!   then cycle through the loop.
 
    if (ierr /= 0) then
      write(*,*) 'Error, invalid input.'
      cycle interactive_loop
    end if
 
!   Compute area.  The ** means "raise to a power."
 
    area = 2 * pi * (radius**2 + radius*height)
 
!   Write the input variables (radius, height)
!   and output (area) to the screen.
 
    write (*,'(1x,a7,f6.2,5x,a7,f6.2,5x,a5,f6.2)') &
      'radius=',radius,'height=',height,'area=',area
 
    yn = ' '
    yn_loop: do
      write(*,*) 'Perform another calculation? y[n]'
      read(*,'(a1)') yn
      if (yn=='y' .or. yn=='Y') exit yn_loop
      if (yn=='n' .or. yn=='N' .or. yn==' ') exit interactive_loop
    end do yn_loop
 
  end do interactive_loop
 
end program cylinder
```

Saved the file as **cylinder.f90**, then I compiled the code w/ gfortran by typing
```
$ gfortran cylinder.f90 -o cylinder.out
```

Now after it was compiled, I ran the executable from terminal by typing 
```
$ ./cylinder.out
```

The problem is the code works for any dimensions except for multiples of 10, so if you enter 10, 10, or 10, 20, or 30, 100...etc. the answer will be ******?!!!!!!
Why is that? Anyone knows?

---

### Post by lisati on 2013-03-08
*Thread moved to **Programming Talk**.*

It has been a while since I've done any kind of Fortran programming (several [s]years[/s] decades) but that looks almost as if the width of a field description in a FORMAT statement is too small or some such problem if you're getting ****** as an output.

---

### Post by gaitonde on 2013-03-09
The problem is in the following write statement.

    write (*,'(1x,a7,f6.2,5x,a7,f6.2,5x,a5,f6.2)') &
      'radius=',radius,'height=',height,'area=',area
 
You use f6.2 for area.  This format provides proper output upto a maximum positive value of 999.99.  
If the answer is higher than this value, then the output will be ******.
This is standard Fortran behaviour.

Increase the capacity of the format, say to something like f12.6, and the problem will be mitigated.
Of course, you can always provide an input that leads to a result higher than what the format can handle.
You may use the 'E' descriptor instead of the 'F' to mitigate the problem further.

Hope this helps.

---

### Post by iMac71 on 2013-03-10
I've rewritten your code without the loop (that's however easy to insert again, if you like it) using a subroutine for formatting the output:```
program cylinder
implicit none
real :: radius, height, area
integer :: ilog10_r, ilog10_h, ilog10_a ! the integer parts of the common logarithms are useful
                                        ! for formatting the output
real, parameter :: pi = 3.141592654
print *, "Enter the radius and the height: "
read *, radius, height
area = 2 * pi * (radius**2 + radius * height)
ilog10_r = int(log10(radius))
ilog10_h = int(log10(height))
ilog10_a = int(log10(area))
call pprint (radius, ilog10_r, height, ilog10_h, area, ilog10_a)
end program cylinder

subroutine pprint (r, il_r, h, il_h, a, il_a)
implicit none
real :: r, h, a
integer :: il_r, il_h, il_a
character (2) :: r_fmt
character (2) :: h_fmt
character (2) :: a_fmt
! for the trick of how to convert numbers to strings, see here:
! http://www.eng-tips.com/viewthread.cfm?qid=37205
write (r_fmt, '(i2)') il_r + 4
write (h_fmt, '(i2)') il_h + 4
write (a_fmt, '(i2)') il_a + 4
write (*, '(1xa7f'//r_fmt//'.2,5xa7f'//h_fmt//'.2,5xa7f'//a_fmt//'.2)') &
    "radius=", r, "height=", h, "area  =", a
end subroutine pprint
```

---

### Post by PC_load_letter on 2013-03-10
Thanks guys you're awesome. It's not my code, I copied it from a Wikipedia page. 
If I have a choice, I'll probably not choose Fortran to learn at this time, but Fortran syntax is used to write custom scripts in a software used at the company I work for. 

Thanks again guys, and sorry for posting at the wrong forum.

---

### Post by iMac71 on 2013-03-11
keep in mind that the pprint subroutine isn't specific of fortran: I wrote it in that programming language since in this thread we were discussing about fortran, but, with a bit of code modifications, it can be easily translated into any other programming language that allows the formatted output.

---

