---
title: "makefile problem"
date: 2012-09-13
forum: Programming Talk
---

### Post by snail100 on 2012-09-13
hello,
i am new to c programming.
i have a question regarding make file: i want to link 3 simple files +makefile
----------------------------------------------- 
main.c

#include <stdio.h>
#include "goodbye.h"
    void main()
    {
    
        goodbye();
        hello();
        
    }
--------------------------------------------------------------------
goodbye.h

void goodbye();
void hello();
-------------------------------------------------
goodbye.c

#include<stdio.h>
    void goodbye()
    {
        printf("goodbye\n");
    }
    void hello()
    {
        printf("hello\n");
    }
----------------------------------------------------
makefile

all: goodbye.o main.o 
    gcc  -ansi -o goodbye.o main.o
goodbye.o: goodbye.c
    gcc  -ansi -c goodbye.c                
main.o: main.c goodbye.h
    gcc  -ansi -c main.c 

-----------------------------------------------
then, i run the makefile and the compiler print:

gcc  -ansi -c goodbye.c                
gcc  -ansi -c main.c 
gcc  -ansi -o goodbye.o main.o
main.o: In function `main':
main.c:(.text+0x7): undefined reference to `goodbye'
main.c:(.text+0xc): undefined reference to `hello'
collect2: ld returned 1 exit status
-------------
i dont understand why the fuctions undefined????????


thanks .

---

### Post by Bachstelze on 2012-09-13
Read about how to use the -o flag in the gcc manual.

Also, main() returns int, not void.

---

### Post by safarin on 2012-09-13
Hi snail10.. I think you should use code function in Message box to code your code.. It is really hard to read it...

Secondly.. you got that problem because the compiler cannot find your header file...

you can use option -I to include your header file..

---

### Post by MG&amp;TL on 2012-09-13
> **safarin said:**
> Secondly.. you got that problem because the compiler cannot find your header file...
 
you can use option -I to include your header file..
 
I thought GCC & co. looked in the current directory for header files, then in the system-defined include paths, then in the paths defined by the -I flags. Perhaps I'm mistaken? (windows system at the mo, so can't test.)

---

### Post by Bachstelze on 2012-09-13
> **safarin said:**
> 
Secondly.. you got that problem because the compiler cannot find your header file...


No.

---

### Post by safarin on 2012-09-13
> **Bachstelze said:**
> No.

Sorry if I got wrong... but seem main.o cannot be create because it does'nt find the function that it need..

---

### Post by Bachstelze on 2012-09-13
> **safarin said:**
> Sorry if I got wrong... but seem main.o cannot be create because it does'nt find the function that it need..

Yes, but the problem is at the linking stage, not at the compilation one. So it has nothing to do with the headers. Remember that a header contains only the prototype of a function, not its code. Here it's the code that cannot be found.

---

### Post by safarin on 2012-09-13
> **Bachstelze said:**
> Read about how to use the -o flag in the gcc manual.

Also, main() returns int, not void.

Hmmm.. you are correct...

problem with his 

int main(void) and -o flag.. 

:popcorn:

---

### Post by Some Penguin on 2012-09-15
...and normally you wouldn't be explicitly giving (incorrect...) gcc lines when when building the individual object files, anyway, since the implicit rules suffice.

See section 2.5, for instance.
[http://www.gnu.org/software/make/manual/make.html#Implicit-Rules]("http://www.gnu.org/software/make/manual/make.html#Implicit-Rules")

---

### Post by Bachstelze on 2012-09-15
> **Some Penguin said:**
> ...and normally you wouldn't be explicitly giving (incorrect...) gcc lines when when building the individual object files, anyway, since the implicit rules suffice.

The gcc lines that generate the object files are correct.

---

