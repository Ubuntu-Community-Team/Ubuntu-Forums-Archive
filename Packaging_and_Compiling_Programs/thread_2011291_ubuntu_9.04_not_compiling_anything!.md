---
title: "ubuntu 9.04 not compiling anything!"
date: 2012-06-26
forum: Packaging and Compiling Programs
---

### Post by GhettoNinja06 on 2012-06-26
**So I just installed ubuntu 9.04 on my HP dm4 laptop and just tried compiling a simple program but get tons of errors that I shouldn't. Here's the program.**
 
 
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
 
#define SEED 35791246
 
main(int argc, char* argv)
{
int trials = 0;
double x,y;
int i,count = 0; /* # of points in the 1st quadrant of unit circle */
double z;
double pi;
printf("Enter the number of trials used to estimate pi: ");
scanf("%d", & trials);
/* initialize random numbers */
srand(SEED);
count = 0;
for (i = 0; i < trials; i++) {
x = (double) rand() / RAND_MAX;
y = (double) rand() / RAND_MAX;
z = x * x + y * y;
if (z <= 1) count++;
}
pi = (double) count / trials * 4;
printf("Number of trials = %d , Estimate of pi is %g \n",trials,pi);
}
 
 
**And these are the errors I keep getting..**
 
**montecarlo.c:1: error: expected '=', ',', ';', 'asm' or '_attribute_' before '<' token**
**In file included from /usr/include/stdlib.h:320,**
**from montecarlo.c:5:**
**/usr/include/sys/types.h:35: error: expected '=', ',', ';', 'asm' or '_attribute_' before 'u_char'**
**montecarlo.c: In function 'main':**
**montecarlo.c:61: warning: implicit declaration of function 'printf'**
**montecarlo.c:61: warning: incompatible inplicit declaration of built-in function 'printf'**
**montecarlo.c:63: warning: implicit declaration of function 'scanf'**
**montecarlo.c:63: warning: incompatible inplicit declaration of built-in function 'scanf'**
 
What can I do to correct this? The same program compiles just fine at school.

---

### Post by GhettoNinja06 on 2012-06-26
Actually, I'd honestly would rather use a newer version of Ubuntu like 12 or something. I had 12 working perfectly with my wireless, screen dimness, bluetooth, sound. But would installing a new version of ubuntu be a bad idea when I try to compile programs at school on ubuntu 9.04?

---

### Post by nipunshakya on 2012-06-26
What are u using to compile the codes? are u using gcc from the terminal or some ide?
have u tried to type ```
gcc <filename>
``` in terminal?

---

### Post by youknowme on 2012-06-26
> **GhettoNinja06 said:**
> **So I just installed ubuntu 9.04 on my HP dm4 laptop and just tried compiling a simple program but get tons of errors that I shouldn't. Here's the program.**
 
 
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
 
#define SEED 35791246
 
main(int argc, char* argv)
{
int trials = 0;
double x,y;
int i,count = 0; /* # of points in the 1st quadrant of unit circle */
double z;
double pi;
printf("Enter the number of trials used to estimate pi: ");
scanf("%d", & trials);
/* initialize random numbers */
srand(SEED);
count = 0;
for (i = 0; i < trials; i++) {
x = (double) rand() / RAND_MAX;
y = (double) rand() / RAND_MAX;
z = x * x + y * y;
if (z <= 1) count++;
}
pi = (double) count / trials * 4;
printf("Number of trials = %d , Estimate of pi is %g \n",trials,pi);
}
 
 
**And these are the errors I keep getting..**
 
**montecarlo.c:1: error: expected '=', ',', ';', 'asm' or '_attribute_' before '<' token**
**In file included from /usr/include/stdlib.h:320,**
**from montecarlo.c:5:**
**/usr/include/sys/types.h:35: error: expected '=', ',', ';', 'asm' or '_attribute_' before 'u_char'**
**montecarlo.c: In function 'main':**
**montecarlo.c:61: warning: implicit declaration of function 'printf'**
**montecarlo.c:61: warning: incompatible inplicit declaration of built-in function 'printf'**
**montecarlo.c:63: warning: implicit declaration of function 'scanf'**
**montecarlo.c:63: warning: incompatible inplicit declaration of built-in function 'scanf'**
 
What can I do to correct this? The same program compiles just fine at school.

These are only warnings - you should still end up with an executable program

---

### Post by AndrewX192 on 2012-06-27
> **GhettoNinja06 said:**
> Actually, I'd honestly would rather use a newer version of Ubuntu like 12 or something. I had 12 working perfectly with my wireless, screen dimness, bluetooth, sound. But would installing a new version of ubuntu be a bad idea when I try to compile programs at school on ubuntu 9.04?

I highly recommend upgrading from 9.04, as it is unsupported and will not receive any updates. You shouldn't notice any significant differences between the older release and a newer release with the level of code complexity you are dealing with.

---

### Post by nipunshakya on 2012-06-27
Im with Andrew on this... upgrade your machine or make a fresh installation of 12.04... because your code compiled inside my machine without an inch of error detection....

---

### Post by oldos2er on 2012-06-27
Moved to Packaging and Compiling Programs.

---

