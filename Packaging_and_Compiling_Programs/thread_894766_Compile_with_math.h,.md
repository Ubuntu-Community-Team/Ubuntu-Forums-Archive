---
title: "Compile with math.h,"
date: 2008-08-19
forum: Packaging and Compiling Programs
---

### Post by 7raTEYdCql on 2008-08-19
How do i cmpile when i have #include<math.h>. Talking about C, and compiling with gcc.

How do you compile with getch(), and clrscr() functions used. It does not compile by the simple technique i know.

gcc 123.c -o 123
./123
This is what i use. Any additions for the above programs to work???

---

### Post by LaRoza on 2008-08-19
> **i.mehrzad said:**
> How do i cmpile when i have #include<math.h>. Talking about C, and compiling with gcc.

How do you compile with getch(), and clrscr() functions used. It does not compile by the simple technique i know.

To use math.h you have to use the "-lm" flag.

```

gcc -lm ...

```

getch() and clrscr() are DOS specific and are not cross platform.

If you have to use them, you can use getchar() and system("clear") in their place then switch them out when you are submitting it.

You could use other libraries like ncurses, but that would be overkill and not worth it (because your instructor will be using Windows and the tasks are simple)

---

### Post by 7raTEYdCql on 2008-08-26
getchar() and getch() are not the same.

Suppose i want to enter onto the screen such that i get stars displayed(much like what we do when we enter our email id's), there getchar will not work. I have to use getch. How is it done???

---

### Post by 7raTEYdCql on 2008-08-26
If conio.h is not a standard library on linux, then where do i get all the functions that conio.h has in my program?

Are these headar files valid on linux machines:
ctype.h
math.h
stdlib.h
string.h
graphic.h
time.h

Are there any differences when compiling for these header files?
I know that for math.h we use the -lm options as well. What about the others.

---

### Post by WW on 2008-08-27
> **i.mehrzad said:**
> 
Are these headar files valid on linux machines:
ctype.h
math.h
stdlib.h
string.h
graphic.h
time.h

All except graphic.h are standard.
> **i.mehrzad said:**
> 
Are there any differences when compiling for these header files?
I know that for math.h we use the -lm options as well. What about the others.
Except for math.h, which requires -lm, no special compiler options are needed when you use the standard headers and libraries.

---

### Post by y-lee on 2008-08-27
> **i.mehrzad said:**
> If conio.h is not a standard library on linux, then where do i get all the functions that conio.h has in my program?

I have saw this question several times on various forums and looked around and found [a Linux "conio.h" ]("http://www.gerald-friedland.de/projects_old.html"). I have not had a chance to use this or test it so I do not know how well it works.

---

### Post by 7raTEYdCql on 2008-08-27
what do i do in the case of graphic.h?

---

