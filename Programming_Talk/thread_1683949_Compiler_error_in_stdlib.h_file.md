---
title: "Compiler error in stdlib.h file"
date: 2011-02-08
forum: Programming Talk
---

### Post by newport_j on 2011-02-08
After getting a very complicated program to compile this error shows up and it is in a header file.
 
 
[FONT=Courier New][SIZE=3]In file included from merge.c:10:[/SIZE][/FONT]
[SIZE=3][FONT=Courier New]/usr/include/stdlib.h:691: error: expected identifier or ‘(’ before ‘__extension__’[/FONT][/SIZE]
 
 
[FONT=Courier New]It is complaining about the header file stdlib.h on line 691. That header file works fine on all of my other programs. I am not sure why the compilers complaining here and now.[/FONT]
 
 
[FONT=Courier New]The line number 10 in merge.c file is only where stdlib.h is included. [/FONT]
 
 
[FONT=Courier New]Any help appreaciated. Thanx in advance.[/FONT]
 
[FONT=Courier New]N_J[/FONT]

---

### Post by MadCow108 on 2011-02-08
stdlib.h itself is fine. your own code is buggy

probably some syntax error before including stdlib.h
e.g. a missing closing brace

---

### Post by newport_j on 2011-02-08
Okay, thank you. I will check it.
 
 
N_J

---

