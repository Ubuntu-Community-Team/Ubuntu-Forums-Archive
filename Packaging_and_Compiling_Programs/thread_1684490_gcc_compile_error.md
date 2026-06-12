---
title: "gcc compile error?"
date: 2011-02-09
forum: Packaging and Compiling Programs
---

### Post by Anticrombie on 2011-02-09
I am going through a C programing course in college right now. The first two programs I had to write worked compiled and ran fine in gcc. When I went to compile my latest code I came up with this error:

```
/tmp/ccRDldOz.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

This is the code for the program:
```
/*

* Programmer: XXXX     Date due: February 9,2011

* Instructor: XXX                 Class:EGT102

* HW04 Programming Pg.70 Problem 1 

*

* Program that stores the values ‘x’ and 76.1 in seperate

* memory cells*/

 

#include <stdio.h>                /* printf, scanf definitions */

int

main(void)

{

       char letter;              /* input for letter.*/

       double num;               /* input for number. */

 

                    /* Prompt for user input and scan. */

                       printf("Enter a character> ");

                       scanf("%c",&letter);

                       printf("Enter a number> ");

                       scanf("%lf",&num);

                              

                    /* Display the results. */

printf("The character is ‘%c’.\n The number is %.1f.\n", letter, num);

return (0);

}
```

I would like to find out where the problem is. I ran the code in Turbo C++ via DOSBox with no problems. Any help would be appreciated.

---

### Post by anglican on 2011-02-09
> **Anticrombie said:**
> I am going through a C programing course in college right now. The first two programs I had to write worked compiled and ran fine in gcc. When I went to compile my latest code I came up with this error:

```
/tmp/ccRDldOz.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```I would like to find out where the problem is. I ran the code in Turbo C++ via DOSBox with no problems. Any help would be appreciated.Have you by any chance called this program <something>.cpp (or some other extension other than .c)? If so you can either rename it to <something>.c or add the option -lstdc++ to gcc.

H

---

### Post by psusi on 2011-02-09
Yea, it looks like you are trying to compile the program as C++, then link as C.

---

### Post by Anticrombie on 2011-02-10
> **anglican said:**
> Have you by any chance called this program <something>.cpp (or some other extension other than .c)? If so you can either rename it to <something>.c or add the option -lstdc++ to gcc.

H

Wow, thanks, I can't believe I didn't catch that.

---

