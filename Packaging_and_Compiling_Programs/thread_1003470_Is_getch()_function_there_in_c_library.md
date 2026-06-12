---
title: "Is getch() function there in c library?"
date: 2008-12-06
forum: Packaging and Compiling Programs
---

### Post by abhilashm86 on 2008-12-06
i tried most of programs using getch() function and i also added <stdlib> library but compiler throws an error,saying getch() is not defined,how to use getch() function?

---

### Post by kcode on 2008-12-08
getch() is not present in glibc. In turboc, it is declared in conio.h, which is not present in glibc. Alternatively you can use getchar().

---

### Post by lensman3 on 2008-12-11
Build your own getc using getc or getchar in a macro.

#define getch getc

Years ago we built a getch.c as a Ratfor primative and it looked like->

/* Get next input character from stream  */

#include <stdio.h>
#include "ratdef.h"
#include "ofiles.h"

char getch( char *c, filedes fd )
   {
   *c = (char) getc( fbuf[fd] );
   return( *c );
   }

---

### Post by meson2439 on 2008-12-11
I'm tired of this getch() question. lensman3, kcode and many others have given many alternatives for getch(). The other is using ncurses. Abhilashman you should look at the solutions in the other threads that you had started. How many times have I told you not to use getch(). This function are no longer used. Adapt plz. #-o

---

### Post by MGaddict2000 on 2009-03-29
we would adapt, but a good alternative has not been presented. New programmers to linux were not taught crossplatform programming. You need to give a simple, explanation mabey with some examples, on how the same task is accomplished in linux then all you have to do is refrence that explanation. We can't find one. All the threads just say, "get rid of conio.h, clrscr, getch, and kbhit. But that doesn't allow the program to run. getch() is used for a lot more then just a pause at the end of the program and clrscr is used for a heck of a lot more then just starting the program. The other explanation is to use another library that is present in linux but nobody gives an explanation as to how. okay, so do I have to work my function in a completely new way or is there just an alternative function to call to do the exact same thing? Also, a lot of windows programmers don't understand scripts, how to write them, or how to use them. Where can we get started? Saying "Make a script" to a windows user means nothing. This is why a lot of people mess with linux for a short period of time and then go back to windows. If somebody is trying to use conio.h or some other windows header, they obviously don't understand the intracacies of linux and need a barny style lesson. If one exists, where can they find it? I wish somebody would create a wiki on windows to linux programming for beginners. Then you could just reference that whenever somebody asks what you concider to be a, "stupid" question. It's not a lack of adapting, its a lack of ignorance. Ignorance can be overcome, defiance can't.

---

### Post by jpgrms on 2011-11-29
relax guys...

[http://wesley.vidiqatch.org/code-snippets/alternative-for-getch-and-getche-on-linux/](http://wesley.vidiqatch.org/code-snippets/alternative-for-getch-and-getche-on-linux/)

---

