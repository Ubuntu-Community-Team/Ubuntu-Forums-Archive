---
title: "Help in C"
date: 2009-07-05
forum: Programming Talk
---

### Post by Alias1407 on 2009-07-05
Hi Guyz,

I am learning C and to say the least I need some help with a program that will create a random number and then you have to guess the number...
Here is the program source code...

```
/*
 *      intguess.c
 *      
 *      Copyright 2009 Stewart Malik <mali0037@gmail.com>
 *      
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 */


#include <stdio.h>
#include <ctype.h>

int main(int argc, char* argv)
{
	/* Clear the screen */
	system("clear");
	
	/* Initialize variables and set the random value */
	srand(time(NULL));
	int iRand = 0;
	iRand = rand() % 10 + 1;
	int iStdin = 0;
	
	printf("%d\n", iRand);
	
	/* Print to screen and collect variables */
	printf("Take a guess at a number between 1 and 10!!\t");
	scanf("%d", &iStdin);
	
	/* Perform calculations and print to screen */
	if(isdigit(iStdin) && iStdin == iRand)
		printf("Congratulations\n\n");
	else
		printf("You were wrong at guessing the number. Better luck next time\n");
		printf("The number was %d\n\n", iRand);			
		
	return 0;
}
```

I want it to tell me when I am right, so to check my answer i have put a little hack in it to tell me what the random number is before i answer, however when i put in the already know answer it tells me i'm wrong.

What is the problem here?

---

### Post by Tony Flury on 2009-07-05
the isdigit function call works on a character variable (type char) - you are testing it on an integer (type int).

you need to find another way of checking that they entered a valid number - if that is what you are trying to do.

---

### Post by jimmio on 2009-07-05
1. %d is a double, you're using integers. Replace all %d with %i.
2. Your if statement. When there's multiple lines you need brackets, and I tend to use them no matter what because it doesn't hurt anything.
```
if(isdigit(iStdin) && iStdin == iRand)
{
	printf("Congratulations\n\n");
}
else
{
	printf("You were wrong at guessing the number. Better luck next time\n");
	printf("The number was %d\n\n", iRand);			
}

```
3. You're testing an integer in a character function call like Tony Flury said. If there's only one character, it will show as a number, so really, it should work fine without that check.

You're doing great though, I remember the troubles I had learning C :P

---

### Post by Alias1407 on 2009-07-05
I changed my %d to %i, but it still isn't working, here is the output of what i get...

```
2
Take a guess at a number between 1 and 10!!	2
You were wrong at guessing the number. Better luck next time
The number was 2
```

---

### Post by Compyx on 2009-07-05
> **jimmio said:**
> 1. %d is a double, you're using integers. Replace all %d with %i.


No, '%d' means decimal, '%g' means double. See `man 3 printf' for further details.

---

### Post by jimmio on 2009-07-05
Ah, sorry about that, I always figured %d is double because of i being integer.

Either one would work there though =)

-Jim


Do a little dance... make a little code... get built tonight ;D

---

### Post by PmDematagoda on 2009-07-05
Here is a working copy of your program:-
```
/*
 *      intguess.c
 *      
 *      Copyright 2009 Stewart Malik <mali0037@gmail.com>
 *      
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 2 of the License, or
 *      (at your option) any later version.
 *      
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *      
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 *      MA 02110-1301, USA.
 */


#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <ctype.h>

int main(int argc, char* argv[])
{
  /* Not necessary, you're going to put a value in it anyway, so no inititialisation required. */
  int iStdin, iRand;

  /* Clear the screen */
  system("clear");
	
  /* Initialize variables and set the random value */
  srand(time(NULL));
  iRand = rand() % 10 + 1;
	
  printf("%d\n", iRand);
	
  /* Print to screen and collect variables */
  printf("Take a guess at a number between 1 and 10!!\n");
  scanf("%d", &iStdin);
	
  /* Perform calculations and print to screen */
  if(iStdin == iRand)
    printf("Congratulations\n\n");

  else
    printf("You were wrong at guessing the number. Better luck next time\n");

  printf("The number was %d\n\n", iRand);			
		
  return 0;
}
```
you needed two more headers as well, running gcc with the -Wall option is a good way to reduce the problems with your code.

---

