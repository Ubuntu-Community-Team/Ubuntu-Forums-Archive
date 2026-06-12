---
title: "gfortran interoperability with procedure pointers"
date: 2009-06-05
forum: Programming Talk
---

### Post by alain_hebert on 2009-06-05
We are using gfortran as our default Fortran compiler. We are currently blocked by a "feature" of this compiler. In our system, a c_funptr pointer to an external Fortran procedure is set. Later, this c_funptr pointer is transformed back into a Fortran procedure pointer using c_f_procpointer and this pointer is called. Compilation is successful on ifort and g95 but fail on gfortran. We got the following gfortran compilation error:

Error: Parameter 'sub1' to 'c_funloc' at (1) must be BIND(C)

Any suggestions?

sample code:

   use, intrinsic :: iso_c_binding
   interface
      real function sub2(a,b)
         real,intent(in) :: a, b
      end function sub2
   end interface
   procedure(sub2), pointer :: sub2_pt
   type(c_funptr) :: sub3_pt
   external sub1
   real :: sum
!
   sub3_pt=c_funloc(sub1)
!
   call c_f_procpointer(sub3_pt, sub2_pt)
   sum=sub2_pt(5.,7.)
   print *,'a+b=',sum
   stop
end program main
!
real function sub1(a,b)
   real :: a, b
   sub1=a+b
   return
end function sub1

---

