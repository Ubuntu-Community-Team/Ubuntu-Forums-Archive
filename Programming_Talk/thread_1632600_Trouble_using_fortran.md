---
title: "Trouble using fortran"
date: 2010-11-28
forum: Programming Talk
---

### Post by phildefer on 2010-11-28
Hi,
i have a problem when i compile my program Fortran 90.
That my code :

```

    type toc3
        real, dimension(3) :: A
    end type toc3

integer :: i
type(toc3), intent(out) :: A1, A2
Real, dimension(3) :: k
REAL :: u

    call random_seed
            do i=1,3
                call ramdom_number(u)
                A1(i)=(k(i))*u
                ! unexpected array reference
            end do    

```I don't understand why it doesn't work ! But somethin is wrong :/

---

### Post by gmargo on 2010-11-28
> **phildefer said:**
> 
```

                call ramdom_number(u)

```

Shouldn't the function should be raNdom_number() - N instead of M?

---

### Post by phildefer on 2010-11-28
Oh yes, that a mistake ! Thank you

But, i tried and i have the same message...

---

### Post by gmargo on 2010-11-28
I got it to compile by changing two things: 1) moving the DIMENSION to the A1,A2 declaration, since I don't think the DIMENSION in the toc3 type carries along, and 2) referencing the toc3 type structure correctly.

Here's what I came up with that compiles cleanly with gfortran (Fortran 95):
```

        PROGRAM foo2
        IMPLICIT NONE

        type toc3
                real :: A
        end type toc3

        CONTAINS
        SUBROUTINE randy(A1, A2)
                type(toc3), intent(out), dimension(3) :: A1, A2
                integer :: i
                Real, dimension(3) :: k
                REAL :: u

                call random_seed
                do i=1,3
                        call random_number(u)
                        A1(i)%A = (k(i))*u
                end do
        END SUBROUTINE randy

        END PROGRAM foo2

```

---

### Post by phildefer on 2010-11-28
Yes, it works now ! Thanks a lot.

Just one thing, i know its good, but i don't unterstand why you wirte A1(i)**%A**=(k(i))*u ? 

I have also an another trouble in my program, in other subroutine, i defined :
real :: phi
type(toc3), dimension(3) :: a

a=(/phi,phi, 0./)

With this, i have : "can't convert Real to type(toc3)"
or with
a%v=(/phi,phi, 0./)
i have :"only one part-reference with nonzero rank can be specified".

Thanks you ;)

---

### Post by gmargo on 2010-11-28
> **phildefer said:**
> i don't unterstand why you wirte A1(i)**%A**=(k(i))*u ? 

The TYPE statement creates a [Derived Data Type]("http://en.wikipedia.org/wiki/Fortran_95_language_features#Derived_data_types"), which is similar to a C structure. Individual elements of the Derived Data Type must be addressed by their name.

If I omit the "%A" part, then I get the error: "Can't convert REAL(4) to TYPE(toc3)"

---

### Post by gmargo on 2010-11-28
> **phildefer said:**
> I have also an another trouble in my program, in other subroutine, i defined :
real :: phi
type(toc3), dimension(3) :: a

a=(/phi,phi, 0./)

With this, i have : "can't convert Real to type(toc3)"
or with
a%v=(/phi,phi, 0./)
i have :"only one part-reference with nonzero rank can be specified".

Thanks you ;)

You need the "structure constructor" format:
```

        PROGRAM foo5
        IMPLICIT NONE

        type toc3
                real :: A
        end type toc3

        real :: phi = 1.234
        type(toc3), dimension(3) :: C

        C = (/toc3(phi), toc3(phi), toc3(0.0)/)

        END PROGRAM foo5

```

---

