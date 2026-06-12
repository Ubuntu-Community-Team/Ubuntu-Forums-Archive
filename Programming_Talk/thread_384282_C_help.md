---
title: "C help"
date: 2007-03-14
forum: Programming Talk
---

### Post by byrddw on 2007-03-14
I am taking a C programming course.  I cannot seem to understand what I am doing wrong on a homework problem.  I am to write a program that will show the number of coins (quarters, dimes, nickels, and pennies) in a certain amount.  I am also to use a pointer.  The assignment seemed pretty straint foward, but I am running into an issue.  Every time my program runs through, it is one penny short.  I cannot get it to come with the correct number of pennies.  I am one short every time.  I am using Bloodsheds DevC compiler.  I mention this because a freind of mine in the course is using the same compiler, and he is having the same problem.  Our programs are completely different (but accomplishing the same functions), yet he is one penny short on every run also.  I am attatching a copy of my program.  Any help would be greatly appreciated.  I've got the program close enough to get an 'A', but I am really curiouse why this is happening.


/*
  Name: Written Assignment 3.B.1
  Copyright: N/A
  Author: Donald W. Byrd
  Date: 12/03/07 15:01
  Description: Total Number of Coins
*/


#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
    void change (float *);      /* Prototype with pointer */
    
    float value;
    
    value = 1.88;               /* Sets first run value */
    
    change (&value);           /* Calls change function */
    
    value = 0.32;              /* Sets second run value */
    
    change (&value);           /* Calls change function for second run */
    
    printf ("\nPlease enter a value: ");  /* Prompts user to enter a */
    scanf ("%f", &value);                 /* number to run through.  */
    
    change (&value);           /* Calls change function for user run */
    
    
    
  
  system("PAUSE");	
  return 0;
}

void change (float *value)
{
     float quarterValue, dimeValue, nickelValue, pennyValue, remainder;
     int quarterNum, dimeNum, nickelNum, pennyNum;
     
     printf ("TOTAL VALUE ENTERED: %5.2f\n\n", *value);
     
     quarterNum = (*value / 0.25);  /* pointer calling value from main () */
     quarterValue = (quarterNum * .25);
     remainder = (*value - quarterValue);
     /* Determines number of quarters */
     
     dimeNum = (remainder / 0.10);
     dimeValue = (dimeNum * 0.10);
     remainder = (remainder - dimeValue);
     /* Determines number of quarters */
     
     nickelNum = (remainder / 0.05);
     nickelValue = (nickelNum * 0.05);
     remainder = (remainder - nickelValue);
     /* Determines number of quarters */
     
     pennyNum = (remainder / 0.01);
     /* Determines number of quarters */
     
     
     
     printf ("The number of quarters is : %2.2i \n", quarterNum);
     printf ("The number of dimes is : %5.2i \n", dimeNum);
     printf ("The number of nickels is : %3.2i \n", nickelNum);
     printf ("The number of pennies is : %3.2i \n\n\n", pennyNum);
    
     
     
}

---

### Post by hod139 on 2007-03-14
First, can you please put all code inside code tags
[ code]  ...  [ /code ]  (without the space)
It preserves indentation and makes it much easier to read.

Second, I haven't looked too closely, but my guess as to the cause of the problem: floating point error.  When dealing with money you should not be using a floating point representation.  Floats are not very accurate, rounding errors occur all the time.

---

### Post by pmasiar on 2007-03-14
> **hod139 said:**
> you should not be using a floating point representation.  Floats are not very accurate, rounding errors occur all the time.

use integer - number of pennies - instead.

---

### Post by Poisson_Pilote on 2007-03-14
The mistake does not come from your IDE - I compiled the program using GCC (command line), the penny-problem is the same.

Same as before - do not use floats, stick to ints.

---

### Post by rplantz on 2007-03-14
> **byrddw said:**
> I am taking a C programming course.  ...  Any help would be greatly appreciated.  I've got the program close enough to get an 'A', but I am really curiouse why this is happening.

First, I applaud you for wanting to understand what's going on even though you got an 'A' on the assignment! When I was teaching, it seemed like most students were concerned only about the grade and paid little attention to understanding the material.

As the others have said here, use ints instead of floats whenever you possibly can. If necessary, scale your values to fit within the int range.

You might want to ask your instructor about this. Only don't give him or her a bad time about it. I was a CS professor for 21 years, and I'm amazed at the number of my colleagues who did not have a good understanding of this. Considering the heavy teaching/research demands on their time, I guess we should cut them a little slack. :)

When you do run into situations where floating point variables are required make sure to use the 'double' type instead of 'float'. That will significantly reduce the amount of round off error. It takes twice as much memory, but that's cheap these days. Assuming you are using a computer with an x86 chip, either 32 or 64 bit, the processor performs all floating point computations in an 80-bit extended floating point format. It then rounds the result to a 64-bit format for 'double', or 32-bit for 'float,' when storing in your variable. So there is no difference in time between the 'float' and 'double' types.

---

### Post by silas_irl on 2007-03-14
As everyone has already stated use int's they are much faster. 

If you can know in advance the size of the number you are taking in you could also limit the int size, when most ints store values up to 4billion, using a short saves 2 bytes and limits size to 65535.  I know in this day and age with lightning fast processors and so much ram available it's a bit pointless, but when writing bigger programs it does a difference.

Use ints, and consider using the % (mod operator).

---

### Post by rplantz on 2007-03-14
> **silas_irl said:**
> As everyone has already stated use int's they are much faster. 
It really is not a matter of speed, but of accuracy. If you don't believe me, try the following C program:
```

#include <stdio.h>
int main()
{
   int x = 16777216
   float y = 16777216.0;
   
   printf("x uses %i bytes and y uses %i bytes.\n", sizeof(x), sizeof(y));
   printf("x = %i and y = %f\n", x, y);
   x = x + 1;
   y = y + 1.0;
   printf("x = %i and y = %f\n", x, y);
   
   return 0;
}

```
In case you don't wish to take the time, a run gives:
```

bob@ubuntu:~/programing$ ./a.out
x uses 4 bytes and y uses 4 bytes.
x = 16777216 and y = 16777216.000000
x = 16777217 and y = 16777216.000000
bob@ubuntu:~/programing$ 

```
In fact, there are times the floats can be used in a "non-traditional" way to increase the speed of your code. Let us say that you are able to use ints (or long ints, or long long ints) for the data you need to manipulate in a count-controlled loop. (Don't forget to do your numerical analysis to ensure there is no overflow.) Most modern processors perform integer and floating point arithmetic in parallel. So make your loop counter a float. (Be sure to use the appropriate inequality for the conditions to terminate the loop.) Now the integer processor is doing your data manipulations while the floating point processor is incrementing (or decrementing) your loop counter.

---

