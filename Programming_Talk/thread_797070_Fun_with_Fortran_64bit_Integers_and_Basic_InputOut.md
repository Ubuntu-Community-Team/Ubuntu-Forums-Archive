---
title: "Fun with Fortran: 64bit Integers and Basic Input/Output"
date: 2008-05-16
forum: Programming Talk
---

### Post by Shining Arcanine on 2008-05-16
I am having trouble compiling a Fortran program that I had originally written in C (that saved days of development) and then translated to Fortran 90.

I am compiling my program with Sun's compiler on my university's a Sun-Fire-V440 server. Here is what I am getting from the Unix shell:

> bash-2.05$ f90 rand.f90 

        INTEGER*8, PARAMETER :: A = 3935559000370003845, C = 2691343689449507681
                                    ^                                            
"rand.f90", Line = 5, Column = 30: WARNING: This numeric constant is out of range.
                                                             ^                   
"rand.f90", Line = 5, Column = 55: WARNING: This numeric constant is out of range.

f90comp: 135 SOURCE LINES
f90comp: 0 ERRORS, 2 WARNINGS, 0 OTHER MESSAGES, 0 ANSI

I did some internet research and learned that INTEGER*8 is used for 64bit integers in Fortran, so I used that as my type and used the same integers that I used for equivalent constant long long integers in my C program, but when I compile it, I get those warnings stating that the constants are out of range.

Also, I am having trouble with basic input/output.

Here is some Fortran code:

```
	PRINT *, "Please enter a seed: "
	READ *, SEED
```

Here is the equivalent C code:


```
	printf("Please enter a seed: ");
	scanf("%llu", &seed);
```

Here is the output of the Fortran code, using 5 as an input:

>  Please enter a seed: 
5

Here is the output of the C code, using 5 as an input:

> Please enter a seed: 5

There are two characters being printed by my Fortran that should no be printed, namely the space at the start of the output and the newline at the start of the input.  I have been banging my head trying to find a way to fix this in my Fortran programs for months. Does anyone know how to fix this?

Edit: Internet browsers trim the space at the beginning of the output, so you will not see it, but it is there.

---

### Post by Bichromat on 2008-05-17
You need to add the _8 suffix to your constants if you want them to be of kind=8, just like you have to use "d0" when you want double precision.

For your input/output problem, well, this is fortran, I/O is poor. print * and write (*,*) end with a newline by default.

Edit : correction. You can prevent a write statement from printing a newline using '$' in your format string :
```

write (*, '(A$)') "Please enter a seed: "

```

---

### Post by Shining Arcanine on 2008-05-18
That worked. Thanks a bunch.

By the way, do you know how to get rid of the white space that Fortran outputs at the beginning of a line, but not its newline? I have some statements that just output information, so I want them to end with a newline, but not start with a space.

---

### Post by Bichromat on 2008-05-18
> **Shining Arcanine said:**
> That worked. Thanks a bunch.

By the way, do you know how to get rid of the white space that Fortran outputs at the beginning of a line, but not its newline? I have some statements that just output information, so I want them to end with a newline, but not start with a space.

If you specify a format, there should be no space. E.g. '(A)' for a single string.

---

### Post by Shining Arcanine on 2008-05-18
You are right, although it seems that I have one last input/output problem. I have the following statement:

```
WRITE (*, '(A, I9.1, A, I20.1)') "#", I, " is ", RAND(X)
```

Here is an example of its output:

> #        0 is   342168685574150284

If I do not put a 9 or something greater in magnitude than what I expect to use after the first I, I get asterisks because it will not exceed the field width. However, if I do put a large enough magnitude after the I, I get spaces. Is there any way, or more specifically, any easy way to switch to C's behavior without resorting to writing hundreds of lines of code to get subroutines that will behave in this manner?

---

### Post by Bichromat on 2008-05-18
Do you really need C-style output ? Fortran was designed for number crunching, not fancy I/O. You can remove the padding spaces, but it's ugly. You have to print the length of your number in a string, then use it as part of your format :

```

integer :: number=134234
character(len=2)      :: format_str
write (format_str, '(i2)') int(log10(1.d0*number))+1

write (*, '(A, I'//trim(format_str)//')') "Number is ", number

```

---

