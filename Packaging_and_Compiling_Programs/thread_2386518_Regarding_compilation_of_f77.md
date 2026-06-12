---
title: "Regarding compilation of f77"
date: 2018-03-07
forum: Packaging and Compiling Programs
---

### Post by dilip.h.n on 2018-03-07
Hello,
I have a Fortran code and when i run the Fortran code as:
f77 abc.f 
i am getting some warning lines as:
MAIN:
Warning on line 198: local variable an never used
Warning on line 198: local variable vx never used
Warning on line 198: local variable vy never used
Warning on line 198: local variable vz never used
Warning on line 198: local variable shx never used
Warning on line 198: local variable shy never used
Warning on line 198: local variable shz never used
Warning on line 198: local variable avau1 never used
Warning on line 198: local variable avau2 never used
Warning on line 198: local variable sumh1 never used
Warning on line 198: local variable phnew never used
Warning on line 198: local variable histt1 never used
Warning on line 198: local variable histth1 never used

but the code runs fine...

But the same code if i run with f95 ie.,
f95 abc.f
i don't get any warning lines and the code runs fine.

Actually, in both f77 and f95 compilers, the code runs fine.. but the warning message comes only with f77 compiler.. which i want to get rid.


1) So why are these warning line coming in f77..??
2) The difference between the output files after running f77 and f95 is that in case of f95 there is tab spaced for each column whereas for f77 it is not tab spaced...and while looking from outside for the f95 output files, it just it looks like nothing is written inside the file/its blank (in case of f95 output file since it has tab indented for each column).

How do i solve these issues..??

Any suggestions are appreciated.

Thank you.

---

