---
title: "FORTRAN 77: an annoying space at the beginning of each OUTPUT line"
date: 2010-08-10
forum: Programming Talk
---

### Post by aureliano13 on 2010-08-10
i need to have my data written in an output file. but when i write them using "write" statement, fortran 77 adds a "space" at the beginning of each line whereas i have to have each line without this "space" at the beginning. 
in addition, my data in output file must include text and integers with different numbers of digits, and integers must be separated by a space from eachother so that each line includes different numbers of integers. THUS, i can't use "format" for writing this data as usual.
PLEASE HELP ME HOW TO GET RID OF THE SPACE AT THE BEGINNING OF EACH OUTPUT LINE!

---

### Post by squaregoldfish on 2010-08-11
No shouting is required here.

You should be able to use a $ in a format string to produce non-advancing I/O, i.e. to write a variable and not move to the next line. This way you should be able to construct your line using multiple write statements.

Steve.

---

### Post by lisati on 2010-08-11
It has been a while since I've used Fortran, so I'm not clued up on possible solutions. It almost sounds like a hanger-on from the days when the first character of an output line was commonly used to control printer spacing. I suspect that there's an option somewhere that you can use to turn this feature off.

---

### Post by aureliano13 on 2010-08-11
steve,
i used a lot of different forms of carriage return and i couldn't find the solution BUT i don't know why when you made me sure to use it again i found the solution!
thanx a lot bro!

also, thanx to the second guy replied my question,,,

---

