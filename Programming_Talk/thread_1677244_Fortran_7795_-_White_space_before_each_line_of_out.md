---
title: "Fortran 77/95 - White space before each line of output"
date: 2011-01-28
forum: Programming Talk
---

### Post by indoze on 2011-01-28
Hello,
I've searched all over the internet for potential solutions to this problem, and while some explanations come close I haven't managed to fully solve my problem.

I have a fortran program, and one subroutine is called at the start to generate an input file using a series of write statements. Part of this subroutine entails reading a comma-separated file to pull variables and write them in the list (3 variables total; 1 integer, 2 real). The write statements I use are similar to this:

```

WRITE (33,*)'Calculated Flux          photo.FLUX'
WRITE (33,*)'Calculated A          'A'
WRITE (33,*)'Calculated B          'B'

```

Where 33 is the unit being called (the input file), and A and B are variables. Since I'm using list-directed output, fortran is inserting a single space at the start of each line, which really screws with the rest of the program this file is generated for. I've tried using different formatting codes (such as '(A)' or '(A$)'), but since these either do not work with my variables or do not form a list, the input still doesn't work.

My question is, is there a way to write to a file in a list format without that starting blank space? Even if it's more complicated (by using explicit formatting), if someone could help me with this I'd be greatly appreciated.

Thank you!

---

### Post by talonmies on 2011-01-28
Ahh FORTRAN I/O: 50 years of computing history in one language....

Basically, when you specific free format output by supplying a * as the format, the FORTRAN runtime is left to its own devices as to how things should be formatted. In the bad, bad old days, output was usually to a printer or teletype terminal, and those usually required some form of control character at line beginning of the line to tell the printer to start printing, put the pen down, or whatever. The space you see is that control character, in its vestigial, post VT52 form.

To get around the problem, use explicit format statements. This should get you started (in the spirit of F77):
```
        PROGRAM TESTING
        REAL A, B
C       
        A = 1.
        B = 2.
C
        WRITE (6,'(A,F8.3)')'Calculated A          ',A
        WRITE (6,*)'Calculated B          ',B
C
        END PROGRAM TESTING
```You should see that the two output lines look different, with the first not containing any start line control character.

---

### Post by indoze on 2011-01-28
Thank you so much! I guess my misunderstanding is needing a second format value for the variable as well. I appreciate your help!

---

