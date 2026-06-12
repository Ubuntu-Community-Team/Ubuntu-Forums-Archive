---
title: "Help with Fortran pls"
date: 2006-03-08
forum: Programming Talk
---

### Post by Alpha_toxic on 2006-03-08
I've got this code in Fortran and I understand almost nothing...
So, can someone translate it for me in C/C++ or even Pascal?
This should be an algorithm for solving linear systems by elimination, but is taken from an old book and this is why it's in Fortran.
Here it goes:
```

    DIMESION A(10),D(10),C(10),B(10)
    N = 10
    DO 10 I = 1,N
    A(I) = -1.
    D(I) = 2.
    C(I) = -1.
 10 B(I) = 0.
    B(1) = 1.
    CALL TRID(A,D,C,B,N)
    WRITE (6,610) (I,B(I),I = 1,N)
610 FORMAT(16H1THE SOLUTION IS /(I5,E15.7))
    STOP
    END
    SUBROUTINE TRID(SUB,DIAG,SUP,B,N)
    DIMESION SUB(30),DIAG(30),SUP(30),B(30)
    IF (N .GT. 1)         GO TO 10
    B(1) = B(1)/DIAG(1)
                          RETURN
 10 DO 11 K = 2,N
    RATIO = -SUB(K)/DIAG(K - 1)
    DIAG(K) = DIAG(K) + RATIO*SUP(K - 1)
 11 B(K) = B(K) + RATIO*B(K-1)
    B(N) = B(N)/DIAG(N)
    K = N
    DO 12 NP1MK = 2,N
    K = K - 1
 12 B(K) = (B(K) - SUP(K)*B(K + 1))/DIAG(K)
                          RETURN
    END

```

---

### Post by Lux Perpetua on 2006-03-08
Umm...where did you get that? "DIMESION" is not a standard word in Fortran...

edit: Ok, it looks like you copied that from a book and made some typos. That should be "DIMENSION."

---

### Post by Alpha_toxic on 2006-03-08
it should be "DIMENSION". i've no idea how I managed to make the same mistake twice...
I think I should go through the source again and look for other mistakes.

---

### Post by Lux Perpetua on 2006-03-08
After fixing that (and fiddling with the indentation a bit), it compiles. By the way: 

sudo apt-get install g77

if you want a free implementation of the Fortran 77 standard. 

Also: [http://www.fortran.com/fortran/F77_std/rjcnf.html](http://www.fortran.com/fortran/F77_std/rjcnf.html)
It's a bit terse, but... :-)

---

### Post by Lux Perpetua on 2006-03-08
I think I've figured it out. It is actually solving a 10 x 10 **tridiagonal** linear system.

---

### Post by lovebyte on 2006-03-08
I seem to remember that 10 years ago I used a program called f2c to change some FORTRAN code into C.  Maybe that could help.

---

### Post by Alpha_toxic on 2006-03-08
[quote=Lux Perpetua]It's a bit terse, but...[/quote]
10x for the link. I don't need to learn Fortran, I just want to understand the algorithm, so it will do just fine ;)
EDIT: on the other hand, it seems there are no examples :(

---

### Post by Alpha_toxic on 2006-03-08
[QUOTE=lovebyte]I seem to remember that 10 years ago I used a program called f2c to change some FORTRAN code into C.  Maybe that could help.[/QUOTE]
I'll take look at this, 10x

---

### Post by Alpha_toxic on 2006-03-08
[QUOTE=Lux Perpetua]I think I've figured it out. It is actually solving a 10 x 10 **tridiagonal** linear system.[/QUOTE]
I hope it does ;)

---

### Post by Lux Perpetua on 2006-03-08
I hope my comments clear things up. Note that "B(K)" is just an array-index operation (the K-th element of B), and that arrays are indexed starting from 1, not 0. ```
[color=red]
C     A, D, C, AND B ARE ALL ARRAYS OF LENGTH 10.
[/color]
      DIMENSION A(10),D(10),C(10),B(10)
      N = 10.
[color=red]
C     A, D, C, AND B REPRESENT A 10 BY 10 TRIDIAGONAL SYSTEM.
C     A IS THE SUBDIAGONAL, D IS THE DIAGONAL, AND
C     C IS THE SUPERDIAGONAL OF THE MATRIX (WHICH WE CALL P).
C     B IS THE RIGHT HAND SIDE OF THE SYSTEM (PX = B).
C     (THE POINT IS TO SOLVE FOR X.)
C     (THEY'VE JUST PICKED SOME VALUES HERE TO ILLUSTRATE THE 
C     PROGRAM. YOU CAN CHECK THAT IT GIVES THE RIGHT ANSWER.)
[/color]
      DO 10 I = 1,N
         A(I) = -1.
         D(I) = 2.
         C(I) = -1.
 10      B(I) = 0.
      B(1) = 1.
[color=red]
C     NOW CALL THE PROCEDURE TO SOLVE THE SYSTEM.
[/color]
      CALL TRID(A,D,C,B,N)
[color=red]
C     NOW PRINT OUT THE ANSWER.
[/color]
      WRITE (6,610) (I,B(I),I = 1,N)
 610  FORMAT(16H1THE SOLUTION IS /(I5,E15.7))
      STOP
      END
[color=red]
C     THIS SUBROUTINE SOLVES A TRIDIAGONAL SYSTEM
C         PX = B
C     FOR X (UP TO 30 EQUATIONS). SUB, DIAG, AND SUP ARE 
C     RESPECTIVELY THE SUBDIAGONAL, DIAGONAL, AND SUPERDIAGONAL
C     OF P; B IS THE RIGHT HAND SIDE, AND N IS THE DIMENSION.
C     THE SOLUTION X IS SIMPLE WRITTEN OVER THE ARRAY B.
C     ALSO, P IS ROW-REDUCED IN PLACE BY GAUSSIAN ELIMINATION.
[/color]
      SUBROUTINE TRID(SUB,DIAG,SUP,B,N)
      DIMENSION SUB(30),DIAG(30),SUP(30),B(30)
      IF (N .GT. 1)         GO TO 10
[color=red]
C     IF N IS <= 1, THEN IT'S A 1 BY 1 SYSTEM AND THE ANSWER IS
C     TRIVIAL. JUST SET B(1) TO THE ANSWER AND EXIT.
[/color]
      B(1) = B(1)/DIAG(1)
      RETURN
[color=red]
C     WE DO THIS IF N > 1. THIS IS THE ROW-REDUCTION
C     (GAUSSIAN ELIMINATION). 
C     WE LOOP FROM K = 2 TO N. (I THINK YOU CAN FOLLOW THIS.)
[/color]
 10   DO 11 K = 2,N
         RATIO = -SUB(K)/DIAG(K - 1)
         DIAG(K) = DIAG(K) + RATIO*SUP(K - 1)
 11      B(K) = B(K) + RATIO*B(K-1)
[color=red]
C     NOW P IS ROW-REDUCED. 
C     THIS IS THE FINAL STEP: BACKSUBSTITUTION.
C     WE KNOW B(N):
[/color]
      B(N) = B(N)/DIAG(N)
[color=red]
C     WE NOW LOOP FROM K = N - 1 TO 1.
C     (NP1MK IS JUST A DUMMY COUNTING VARIABLE; IT'S K WE CARE
C     ABOUT.)
[/color]
      K = N
      DO 12 NP1MK = 2,N
         K = K - 1
[color=red]
C        BACKSUBSTITUTE B(K + 1) TO FIND B(K).
[/color]
 12      B(K) = (B(K) - SUP(K)*B(K + 1))/DIAG(K)
      RETURN
      END

```

---

### Post by Alpha_toxic on 2006-03-08
10x alot. This was EXACTLY what I needed. You saved me hours (or even days) of ](*,) . 10x again.

---

