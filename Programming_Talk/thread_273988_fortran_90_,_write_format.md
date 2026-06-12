---
title: "fortran 90 , write format"
date: 2006-10-09
forum: Programming Talk
---

### Post by arkangel on 2006-10-09
Hi 

I am using ifort 9.0  and i am using  write to a textfile , for one reason,the write sentence  adds an extra blank space at the beginning of the line
this statement 
  write(10,*) '12345678'

produces in the unit 10 file
  " 12345678"   (ignore the quotation marks)instead of 
  "12345678"

how can i erase the exta space?

---

### Post by arkangel on 2006-10-09
to make the idea clear 

i dont know  the lenght of my line

---

### Post by xtacocorex on 2006-10-09
FORTRAN does that, you have to specify an actual format to remove the space.

You would need to do the following for the numbers:
[php]WRITE(10,A8) '12345678'[/php]Since you added the ' around, the formatting is for characters.

---

### Post by roncrump on 2006-11-05
I believe that:
```
write(10,'(a)') '12345678'
```
would do your job - that is without a character string/line length parameter.

Ron.

---

