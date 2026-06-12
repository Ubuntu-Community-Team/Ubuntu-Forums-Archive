---
title: "Need help on this Fortran 77 program"
date: 2008-03-03
forum: Programming Talk
---

### Post by DivineNuker on 2008-03-03
Alrighty, I am working on this program ... this is a homework assignment

I have the entire program completely done..,, but i am struggling on the actual formatting of the output

My output has 4 arrays (already ready), and they have to outputted into a data file (.txt) each array having its own column. So it will be 4 different columns with the array data in each.

I dont know if any of you are familiar with Fortran77.. but um here is the code if you need it. to help me. 

      PROGRAM SINECOMP
      
      REAL A(31), RCONV, B(31), C(31), D(31), CALC
      INTEGER NUM
      NUM =1
      RCONV= 3.141593/180.0

      OPEN(UNIT=30, FILE='SINEX.txt', STATUS='NEW')
      
      DO 11 K=0, 90, 3
      A(NUM) =K
      NUM= NUM+1
11    CONTINUE

      DO 12 I=1, 31
      B(I)= A(I)
      B(I) = B(I) * RCONV
12    CONTINUE

      DO 13 I=1, 31
      C(I)= B(I)
      C(I) = SIN(C(I))
13    CONTINUE

      DO 14 I=1, 31
      X = B(I)
      D(I)=CALC(X)
14    CONTINUE

      WRITE (30,400) A, B, C, D
400   FORMAT (1X,F10.2,10X,F10.4,20X,F10.4,35X,F10.4)


      END
C     -----------------------------------------------------------------
      REAL FUNCTION CALC(X)
      
      REAL X
      CALC =((X-((X**3)/6)+((X**5)/120)-((X**7)/5040)+((X**9)/362880)))
      RETURN
      END

the output file name is SINEX.txt

the output statement is 
FORMAT (1X,F10.2,10X,F10.4,20X,F10.4,35X,F10.4)

now.. when this outputs i get the arrays on the same line instead of in different columns. I have tried everything.. all the formatting commands.. new line.. blah blah.. but i simply cant get it right

Any help will be appreciated

Thanks

---

### Post by DivineNuker on 2008-03-03
wow.. nvm i just got it ^_^

sorry to bother :D

---

### Post by mrphd on 2008-03-03
Why not something like:

WRITE (30,400) (A(I), B(I), C(I), D(I), I=1,31)

400 FORMAT (1X,4(F10.4,4X))

That should work. You can change the format statement if you want a different display format for each column.

---

### Post by DivineNuker on 2008-03-03
wow THANKS!!!

thats even better looking than what i had

wow thanks a million sir

you are a genius :DDD
:popcorn:

---

