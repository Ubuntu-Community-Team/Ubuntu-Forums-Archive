---
title: "Fortran:  Reading string with spaces?"
date: 2011-04-22
forum: Programming Talk
---

### Post by castiglione on 2011-04-22
Hello,
 
I was wondering if there was any way to read a string with spaces in it in Fortran?  I attempted to use "read(*,*)" and got a problem:  Typing code akin to:
 
character*20 istring
read(*,*) istring
 
and running it results in the program truncating the string after the first space (" ") encountered, i.e. if one were to type in:
 
"My dog has flees", the program would only read "My".
 
Is there anything that can be done with formating, etc.?
 
Thanks in advance!
 
c

---

