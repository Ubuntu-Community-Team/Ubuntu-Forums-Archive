---
title: "[C programming] multiplication table"
date: 2009-09-07
forum: Programming Talk
---

### Post by gotenks05 on 2009-09-07
I am currently taking a C programming class and I am having a hard time with a certain program.  The program is supposed to create a multiplication table that has the column headings tabbed over and the row headings on the left going down.  Well, I have created a program to do that, but the paper I says that I need to use nesting loops for the rows instead of a loop for each row.  How can I accomplish this?

This is source code I have typed up and should give an idea of what the multiplication table should look like.

```

/*
* Author:  B.C.
* Date:  9/7/09
* Version: 0.0.1
* Class: CIT 131 / Fall 2009
* Assignment: Create a program that prints out a multiplication table.
*/

#include <stdio.h> /* import standard input/output library */B	

int main()
{
	int num = 10; /* declare variable and set it to ten for the column headings */
	int num2 = 10; /* declare variable for multiplying the numbers */
	int product; /* declare variable to hold the products of each multplication, before it is displayed */
	int num3 = 10;

	for (num; num >= 1; num--) /* use a for loop to create column headings */
	{
		printf("\t%d", num); /* display current value of the num variable */
	}

	printf("\n"); /* insert newline, in order to create row headings */


	/* the following loops and their nested loops display a row heading and displays the products of the row heading and the corresponding column heading */
	for (num3; num3 >= 10; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 10; num2--) /* display one product */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten for the next row */


	}

	num3 = 9; /* ensure num3 is set to nine */

	for (num3; num3 >= 9; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 9; num2--) /* display two products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 8; /* ensure num3 is set to eight */

	for (num3; num3 >= 8; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 8; num2--) /* display three products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 7; /* ensure three is set to seven */

	for (num3; num3 >= 7; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 7; num2--) /* display four products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 6; /* ensure num3 is set to 6 */

	for (num3; num3 >= 6; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 6; num2--) /* display five products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 5; /* ensure num3 is set to five */

	for (num3; num3 >= 5; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 5; num2--) /* display six products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 4; /* ensure num3 is set to four */

	for (num3; num3 >= 4; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 4; num2--) /* display seven products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 3; /* ensure num3 is set to three */

	for (num3; num3 >= 3; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 3; num2--) /* display 8 products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 2; /* ensure num3 is set to two */

	for (num3; num3 >= 2; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 2; num2--) /* display nine products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

		num2 = 10; /* reset num2 back to ten */


	}

	num3 = 1; /* ensure num3 is set to 1 */

	for (num3; num3 >= 1; num3--)
	{
		printf("%d", num3);

		for (num2; num2 >= 1; num2--) /* display ten products */
		{
			product = num2 * num3;
			printf("\t%d", product);
		}
		printf("\n");

	}

	
return 0;
}
```

---

### Post by Finalfantasykid on 2009-09-07
I'm not really understanding your method of doing this.  From what I can tell, the outer for loops are only iterating once, and so are essentially useless.

I'm pretty sure all you need is something like this.

```
for(int i = 0; i <= X_MAX; i++){
   for(int j = 0; j <= Y_MAX; j++){
      // Calculations here
      printf("%d ", calculated_num);
   }
   printf("\n");
}
```I dunno something like that would probably work.

---

### Post by dwhitney67 on 2009-09-07
> **Finalfantasykid said:**
> I'm not really understanding your method of doing this.  From what I can tell, the outer for loops are only iterating once, and so are essentially useless.

I'm pretty sure all you need is something like this.

```
for(int i = 0; i <= X_MAX; i++){
   for(int j; j <= Y_MAX; j++){
      // Calculations here
      printf("%d ", calculated_num);
   }
   printf("\n");
}
```I dunno something like that would probably work.

You would probably want to initialize the index i to a 1 (not a zero), and also initialize the index j to a 1.

---

### Post by Finalfantasykid on 2009-09-07
Woops, I forgot to initialize j >.<

*fixed*

And I initialized to 0 because I felt like it :P  Why shouldn't 0 count lol

---

### Post by gotenks05 on 2009-09-07
> **Finalfantasykid said:**
> I'm not really understanding your method of doing this.  From what I can tell, the outer for loops are only iterating once, and so are essentially useless.

I'm pretty sure all you need is something like this.

```
for(int i = 0; i <= X_MAX; i++){
   for(int j = 0; j <= Y_MAX; j++){
      // Calculations here
      printf("%d ", calculated_num);
   }
   printf("\n");
}
```I dunno something like that would probably work.

I'm going to try this one right now.  Also, for some reason gcc does not like me to declare variables as integers inside for loops, but Java never complains about it.

---

### Post by Can+~ on 2009-09-07
> **gotenks05 said:**
> I'm going to try this one right now.  Also, for some reason gcc does not like me to declare variables as integers inside for loops, but Java never complains about it.

Maybe because both are completely different things?

Anyway, C89 didn't allow that, I think that C99 does. Compile with [FONT="Courier New"]-std=c99[/FONT].

Edit: Looking at the code, I'm impressed when people find themselves copy+pasting code and changing some variables, never stopping to think "maybe there's a better way to do this".

---

### Post by gotenks05 on 2009-09-07
> **Can+~ said:**
> Maybe because both are completely different things?

Anyway, C89 didn't allow that, I think that C99 does. Compile with [FONT="Courier New"]-std=c99[/FONT].

Edit: Looking at the code, I'm impressed when people find themselves copy+pasting code and changing some variables, never stopping to think "maybe there's a better way to do this".

Actually Java is based on C and looking at the code somebody typed in, they typed the for loop just like a person would in Java.

GCC brings up this message, if I declare variables as integers in for loops

> error: &#8216;for&#8217; loop initial declaration used outside C99 mode


I'm just surprised something like this was assigned, when the chapter does not even discuss something like this, only single loops are discussed and the info going all in one direction instead of two or three different directions.

---

### Post by Finalfantasykid on 2009-09-07
Hmm, thats weird, I thought thats how I did it when I took c, but I am obviously wrong.  I just compiled it now, and I got the same error.  I must be writting too much Java or something ;P.

```
int i;
for(i = 0; i <= Y_MAX; i++){
   int j;
   for(j = 0; j <= X_MAX; j++){
      int calculated_num = i*j;
      printf("%5d", calculated_num);
   }
   printf("\n");
}

```This is a better version of my above code, which has better formatting, and I noticed that X_MAX and Y_MAX were in the wrong for loops.  And this one actually compiles :P

---

### Post by Can+~ on 2009-09-07
> **gotenks05 said:**
> Actually Java is based on C and looking at the code somebody typed in, they typed the for loop just like a person would in Java.

Java was inspired on C. They kept the syntax for the sake of popularity (new syntax = old programmers won't like it), but the fundamental underpinnings of Java are different in every way.

They are both statically typed, but C is unsafe, doesn't have Object "Orientedness" (builtin) and doesn't deal with memory directly (Garbage Collector, pointers are hidden).

But w/e, I got your point.

> **gotenks05 said:**
> GCC brings up this message, if I declare variables as integers in for loops

> **Finalfantasykid said:**
> Hmm, thats weird, I thought thats how I did it when I took c, but I am obviously wrong.  I just compiled it now, and I got the same error.  I must be writting too much Java or something ;P.

Again,

```
~$gcc -std=c99 mycode.c -o myexecutable
```

---

### Post by gotenks05 on 2009-09-08
To make things easier, I decided to use only one for loop. for the top row (aka. column headings) and used while loops for the rows, but it only displays products for the first row.

The following is my updated code
```
/*
* Author:  B.C.
* Date:  9/7/09
* Version: 0.0.1
* Class: CIT 131 / Fall 2009
* Assignment: Create a program that prints out a multiplication table.
*/

#include <stdio.h> /* import standard input/output library */	

int main()
{
	int num = 10; /* declare variable and set it to ten for the column headings */
	int num2 = 10; /* declare variable for the row headings */
	int num3 = 1;  /* set number of rows and columns */
	int num4 = 10; /* set variable for product */

	for (num2; num2 >= num3; num2--) /* this loop creates the column headings */
	{

		printf("\t%d", num2);
	}

	printf("\n"); /* create a new line */

	while (num >= num3) /* This loop labels the rows and displays the product of row * column */
	{

		printf("%d", num);


		while (num4 >= num3)
		{

			int product = num4 * num;
				
			printf("\t%d", product);
			num4--;
		}
		printf("\n");
		num--;
	}
	

	return 0;
}
```

This is the reason why I used the code in the first post.  This would probably be much easier with arrays, but I have only learned arrays in Java, not C.

---

### Post by PandaGoat on 2009-09-08
My advice would be to scratch it all and rewrite it. Learn from your most recent code; don't repeat it.  Start from a clean blank c source file and use for loops.

The problem here is that after the first execution of (not the first iterate, the entire loop)
```

while (num4 >= num3)
{
	int product = num4 * num;
				
	printf("\t%d", product);
	num4--;
}

```
all subsequent executions of this code will cease immediately since you do not reset num4 to 10.  This is why for loops are handy.

---

### Post by gotenks05 on 2009-09-08
> **PandaGoat said:**
> My advice would be to scratch it all and rewrite it. Learn from your most recent code; don't repeat it.  Start from a clean blank c source file and use for loops.

The problem here is that after the first execution of (not the first iterate, the entire loop)
```

while (num4 >= num3)
{
	int product = num4 * num;
				
	printf("\t%d", product);
	num4--;
}

```
all subsequent executions of this code will cease immediately since you do not reset num4 to 10.  This is why for loops are handy.

Thanks for the help on that part.  I now need to have the rows setup in a certain way though, which I doubt is possible in a simple method.

---

### Post by dribeas on 2009-09-08
Also consider using functions to simplify the logic and make it more readable:

```

void print_header();
void multiplication_table();
void multiplication_table_line( int multiplier ); // print the row of multplier*1, multiplier*2...

int main()
{
   print_header();
   multiplication_table();
}

void multiplication_table()
{
   int number = 1;
   for ( number = 1; number < 10; ++number )
   {
      multiplication_table_line( number );
   }
}
/* ... */

```

This way you split the problem in smaller parts. In each function you have to deal with only a subset of the problems and the number of variables you must think of is smaller. The code snippets will be smaller (each function only has a single loop) and will be easier to deal with, you can test the code part by part (implement and test the multiplication_table_line function, and once you have it working, implement the rest... Once you are more familiar with the language you will be able to implement it naturally in a single function (if you want to)

---

### Post by dwhitney67 on 2009-09-08
I don't quite understand what was wrong with the nested for-loop approach?  Whether one declares the ints within the for-loop or outside, it doesn't get any easier.

```

#include <stdio.h>

int main()
{
   for (int i = 1; i < 12; ++i)
   {
      for (int j = 1; j < 12; ++j)
      {
         printf("%3d ", i*j);
      }
      printf("\n");
   }
   return 0;
}

```
As Can+~ indicated, because the declarations are within the for-loop body, such code can only be compiled with a "modern" compiler... ie those that were issued circa 1999.  By default, GCC uses the 1989 standard, which is not capable of interpreting the code above.  To force it to use the 1999 standards, the -std=c99 option must be specified.  Something like:
```

gcc -std=c99 MultTbl.c -o mult_tbl

```

The only thing that this snippet of code is missing above is perhaps user-input (to obtain the max number to operate on), and perhaps the usage of Dribeas' suggestion that the multiplication table be implemented within a function.  But these are not requisites; the basic multiplication given to most of us when we were in primary school can be generated with the code shown above.

What the OP needs to do, IMO, is avoid posting his homework problems on this site, spend a couple of hours practicing his code with different permutations of the same problem, thus hopefully yielding an understanding of the usage of for-loops, while-loops, and the such.  Surely in his text book there is a statement (or two) that a for-loop block can contain additional statements.  Well, another, embedded for-loop is a statement!

---

### Post by gotenks05 on 2009-09-08
> **dribeas said:**
> Also consider using functions to simplify the logic and make it more readable:

```

void print_header();
void multiplication_table();
void multiplication_table_line( int multiplier ); // print the row of multplier*1, multiplier*2...

int main()
{
   print_header();
   multiplication_table();
}

void multiplication_table()
{
   int number = 1;
   for ( number = 1; number < 10; ++number )
   {
      multiplication_table_line( number );
   }
}
/* ... */

```

This way you split the problem in smaller parts. In each function you have to deal with only a subset of the problems and the number of variables you must think of is smaller. The code snippets will be smaller (each function only has a single loop) and will be easier to deal with, you can test the code part by part (implement and test the multiplication_table_line function, and once you have it working, implement the rest... Once you are more familiar with the language you will be able to implement it naturally in a single function (if you want to)

True, it would decrease the work, but I have not learned how to make functions yet.  After all, this is only my second programming language and I learned Java as my first.  I did get things to worked out though.  

> **dwhitney67 said:**
> I don't quite understand what was wrong with the nested for-loop approach?  Whether one declares the ints within the for-loop or outside, it doesn't get any easier.

```

#include <stdio.h>

int main()
{
   for (int i = 1; i < 12; ++i)
   {
      for (int j = 1; j < 12; ++j)
      {
         printf("%3d ", i*j);
      }
   }
   return 0;
}

```
As Can+~ indicated, because the declarations are within the for-loop body, such code can only be compiled with a "modern" compiler... ie those that were issued circa 1999.  By default, GCC uses the 1989 standard, which is not capable of interpreting the code above.  To force it to use the 1999 standards, the -std=c99 option must be specified.  Something like:
```

gcc -std=c99 MultTbl.c -o mult_tbl

```

The only thing that this snippet of code is missing above is perhaps user-input (to obtain the max number to operate on), and perhaps the usage of Dribeas' suggestion that the multiplication table be implemented within a function.  But these are not requisites; the basic multiplication given to most of us when we were in primary school can be generated with the code shown above.

What the OP needs to do, IMO, is avoid posting his homework problems on this site, spend a couple of hours practicing his code with different permutations of the same problem, thus hopefully yielding an understanding of the usage of for-loops, while-loops, and the such.  Surely in his text book there is a statement (or two) that a for-loop block can contain additional statements.  Well, another, embedded for-loop is a statement!

I did understand for-loops pretty well from my time learning Java and figured out what I could not do in C syntax.  For example, unless I used the C99 library, which the class does not focus on yet, I cannot declare variables as integers inside a for-loop

As for user input, it was not supposed to get the user input, or for-loops would have indeed been easy to implement then.  The opening post had the code for how the multiplication table needed to be displayed, which I finally figured out.  

Also, I went through the book and the chapter the assignment was for did not discuss anything like this.  The only loops mentioned were single loops.  Yes, I knew an embedded loop/if statement was a nested statement, but since I never attempted it before now, I could not get it displayed right.

I figured it out at least, thanks to pandaGoat suggesting to rewrite the code I previously posted and a fellow classmate, who unknowingly agreed with the same idea I got last night.

---

