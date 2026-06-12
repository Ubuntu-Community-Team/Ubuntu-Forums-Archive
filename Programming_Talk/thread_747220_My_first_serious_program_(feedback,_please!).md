---
title: "My first serious program (feedback, please!)"
date: 2008-04-06
forum: Programming Talk
---

### Post by nvteighen on 2008-04-06
Hi there!
Some of you already know I'm playing around with C. Well, I was wondering if someone could criticize this code, which is maybe my first serious program that actually does something "useful". I'm sure there's a lot to comment and improve on this.

It's a [D'Hondt apportionment]("http://en.wikipedia.org/wiki/D%27Hondt_method") calculator that uses an input file listing how many votes each party has got and prints how many seats do each receive using this algorithm.

(I GPL'ed because... well, you never know if some code of yours can be useful for someone else!)

This is the code:
[PHP]
/*A D'Hondt/Hagenbach-Bischoff Method implementation in C
*
*    Copyright (c) 2008 Eugenio M. Vigo
*
*    This program is free software: you can redistribute it and/or modify
*    it under the terms of the GNU General Public License as published by
*    the Free Software Foundation, either version 3 of the License, or
*    (at your option) any later version.
*
*    This program is distributed in the hope that it will be useful,
*    but WITHOUT ANY WARRANTY; without even the implied warranty of
*    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*    GNU General Public License for more details.
*
*    You should have received a copy of the GNU General Public License
*    along with this program.  If not, see <http://www.gnu.org/licenses/>
*
*/


#include <stdio.h>
#include <stdlib.h>

float hb2(int v, int d)
{
	float output;
	output = v / (d + 1); //Droop quota applied
	
	return output;
}

int exam_max(float *q, int n)
{
	int output, i;
	float o;
	
	//Primitive way to choose the largest value from a given list.
	o = 0;
	for(i = 0; i <= n; i++)
	{	
		if(q[i] > o)
		{
			o = q[i];
			output = i;
		}
	}
	
	return output;
}

int main(int argc, char **argv)
{
	FILE *data;
	int c, i, n, tot, tot_real, vtot, a, *seats, *vot;
	float *q, wz;

	if(argc != 2)
	{
		//Exiting if no file specified or if too much arguments used.
		puts("Usage: dhondt FILENAME");
		exit(1);
	}	

	if((data = fopen(argv[1], "r")) == NULL)
	{
		//Opening and testing file. If failed, exiting.
		perror("dhondt");	
		exit(2);
	}

	/*RAII, so initializing variables.
	n = -2 so the last '\n' and 'EOF' characters are not inserted into the vot and seats
	arrays*/
	n = -2;
	tot_real = 0;
	vtot = 0;
	
	/*Check in how many parties will the seats be apportioned by counting the amount of 		integers there are.*/
	while(fscanf(data, "%d", &c) != EOF)
	{		
		n++;
	}
	rewind(data); //Rewinding file.
	
	/*Surely heap can be avoided, but I'm not aware how. So, I'm forced to dynamic allocation
	vot = array of votes by each party
	seats = array of number of seats
	q = quota for each party.*/
	vot = malloc(n * sizeof(int));
	if(vot == NULL)
		exit(3);
	seats = malloc(n * sizeof(int));
	if(seats == NULL)
		exit(4);
	q = malloc(n * sizeof(float));
	if(q == NULL)
		exit(5);

	//The first number in the file will be treated as the total amount of seats.
	fscanf(data, "%d", &tot);
	
	for(i = 0; i <= n; i++)
	{
		fscanf(data, "%d", &vot[i]); //Reading
		vtot += vot[i]; //Calculating total amount of votes
	}
	fclose(data); //Closing the file. We don't need it any longer.
	
	wz = vtot / (tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1
	
	for(i = 0; i <= n; i++)
	{
		seats[i] = (int)(vot[i] / wz); //Seats are integers... you can't have 14.788 seats!
		tot_real += seats[i]; //Calculating amount of seats that have been apportioned.
	}
	
	/*But as D'Hondt uses down-rounding, tot_real will very probably be some seats smaller than 		the total amount of seats we wanted to apportion. Here we use the Hagenbach-Bischoff 		method, a so-called "static" apportionment method: we divide each party's votes by the 		seats it already has plus 1 (Droop quota again!). One seat is given to the party having the 		largest quotient. This is repeated until no more seats are needed to apportion.*/
	if(tot_real < tot)
	{
		for(i = 0; i <= n; i++)		
			q[i] = hb2(vot[i], seats[i]);
		a = exam_max(q, n);
		seats[a]++;
		tot_real++;
	}
	free(q); //Free malloc'd memory.

	for(i = 0; i <= n; i++)
		printf("%d\n", seats[i]);
	
	//Free malloc'd memory.	
	free(vot);
	free(seats);
	return 0;
}
[/PHP]

Input files **must only include integers** and be written like this:
```

TOTAL NUMBER OF SEATS
PARTY A's VOTES
PARTY B's VOTES
PARTY C's VOTES
...

```

Thanks in advance!

---

### Post by LaRoza on 2008-04-06
I haven't tested it, but I assume it does what you say :-)

There are a few issues with the style that I see. These are not hard rules, but may be worth thinking about:

[list]
[*] Your variables pop out of nowhere, maybe declaring them individually at the top of the function, and initializing them there
[*] Many exit points. There are many points in your program where the program can exit. That can get confusing fast. Instead of exiting, perhaps you can print a debug message, and have main() return the exit code. (see code snippet below)
[*] float hb2(int v, int d), what if d is -1?
[/list]


See this structured approach:
[php]
int main(void)
{
    int main = 0;
    int * x = malloc(sizeof(char) * 1000000000000);
    main = x ? 0 : 1;
    return main;
}
[/php]

The program only exits when main(void) ends. The exit value can be changed from 0 (success) if something doesn't go right. Adding messages on errors would help clarify, but your program won't be exiting at random points.

---

### Post by dwhitney67 on 2008-04-06
Personally I like to use the 1999 C-standards when compiling with the gcc compiler so that when I declare variables, I can do so near where the are first used, and I can also initialize them when they are declared.

For instance:
[PHP]int i = 10;

for ( int j = 0; j < i; ++j )
{
  ...
}

int k = i * 2;[/PHP]

The other, and probably more important thing that you need to remember, is that when declaring an array with N slots, you address the array using indices 0 through (N-1).  In your code, there are several places where you are indexing to N.  For example:
[PHP]int exam_max(float *q, int n)
{
    int output, i;
    float o;
    
    //Primitive way to choose the largest value from a given list.
    o = 0;
    for(i = 0; i <= n; i++)
    { 
    ...[/PHP]
In the for-loop above, you should have tested with "i < n", not "i <= n".

Lastly, try to simplify the main program to not perform as many tasks as it does.  Consider modularizing the code (i.e. create functions to perform unique, and repetitive operations).

P.S.  To compile using the 1999 standards, use "gcc -std=c99"

---

### Post by nvteighen on 2008-04-06
@LaRoza:
> **LaRoza said:**
> 
[*] Your variables pop out of nowhere, maybe declaring them individually at the top of the function, and initializing them there
[*] Many exit points. There are many points in your program where the program can exit. That can get confusing fast. Instead of exiting, perhaps you can print a debug message, and have main() return the exit code. (see code snippet below)
[*] float hb2(int v, int d), what if d is -1?
[/list]

[list]
[*] You say to declare and initialize in a single line instead of initializing them the moment before they're being used?
[*] Let me see if I understood what you say: instead of exit();, I should just break the function by calling a return.
[*] If d = -1, we get a pretty division by 0... but I don't see how d could even get a negative value. Maybe I should change all int to unsigned int?
[/list]

---

### Post by nvteighen on 2008-04-06
@dwhitney67:

> **dwhitney67 said:**
> Personally I like to use the 1999 C-standards when compiling with the gcc compiler so that when I declare variables, I can do so near where the are first used, and I can also initialize them when they are declared.

(...)

I see this is a matter of style... Well, I get the idea: declaration and initialization should be as nearest as possible (no matter of I use LaRoza's approach or yours). Thanks!

> The other, and probably more important thing that you need to remember, is that when declaring an array with N slots, you address the array using indices 0 through (N-1).  In your code, there are several places where you are indexing to N.
(...)
In the for-loop above, you should have tested with "i < n", not "i <= n".

I must recognize I forgot to change those i <= n. (There was a moment in which I confused n's function...). Well, changing them to "i < n" leads to initialize it as "n = -1".

> Lastly, try to simplify the main program to not perform as many tasks as it does.  Consider modularizing the code (i.e. create functions to perform unique, and repetitive operations).
I'm going to try that. Yes, I see that e.g. I could create a little function to check whether memory was allocated or not instead of repeating those "if" statements. But if I modularize, I fear I'll create several functions that just will be called once.

> P.S.  To compile using the 1999 standards, use "gcc -std=c99"
Thanks! I'm going to check it out!

---

### Post by dwhitney67 on 2008-04-06
> **nvteighen said:**
> @LaRoza:


[list]
[*] You say to declare and initialize in a single line instead of initializing them the moment before they're being used?
[*] Let me see if I understood what you say: instead of exit();, I should just break the function by calling a return.
[*] If d = -1, we get a pretty division by 0... but I don't see how d could even get a negative value. Maybe I should change all int to unsigned int?
[/list]

For the first bullet, I disagree.  Declare variables closest to where used and initialize them (see my previous posting).

For the second bullet, some people subscribe to the notion that it is best to have one exit point out of a function.  I agree that it does make the code easier to read when doing such.  So, heed LaRoza's advice, and maintain an integer exit-status value that is initialized to zero, but set to another value upon detecting an error.

For the third bullet, yes, always use unsigned values when dealing with array indexes.  They should never be negative values.

---

### Post by LaRoza on 2008-04-06
> **nvteighen said:**
> @LaRoza:


[list]
[*] You say to declare and initialize in a single line instead of initializing them the moment before they're being used?
[*] Let me see if I understood what you say: instead of exit();, I should just break the function by calling a return.
[*] If d = -1, we get a pretty division by 0... but I don't see how d could even get a negative value. Maybe I should change all int to unsigned int?
[/list]

I *prefer* declarations like this:

```

int main(void)
{
    int age;
    int i;
    int counter;

    char * name = malloc(sizeof(char) * 20);
    
    FILE fLog = fopen("log.txt","w");
    //etc
}

```

In my opinion, having variables easy to find an identify is worth the extra lines unless they are obviously related, like an "int i, j, k" declaration (variables used as counters).

You should return at the end of the function, and only at the end of the function. At least, that is what I believe and find to be the most structured. 

I didn't examine the logic of the code, only the look and general flow. I saw division, and a possibility for an error. 

(Keep in mind that I haven't slept for about 28 hours, so I may not give the most coherant code examples)

---

### Post by nvteighen on 2008-04-06
> **LaRoza said:**
> 

You should return at the end of the function, and only at the end of the function. At least, that is what I believe and find to be the most structured.

OK, but that won't prevent the code to be executed. If I do that, I have to include an "if" statement before each function call so it reaches the end of main and returns...

---

### Post by LaRoza on 2008-04-06
> **nvteighen said:**
> OK, but that won't prevent the code to be executed. If I do that, I have to include an "if" statement before each function call so it reaches the end of main and returns...

A function should do one thing only. Don't have main() doing everything. if statements are the most common statements in programming, especially in C :-)

You can look out the ternery operator: [http://cprogramminglanguage.net/c-ternary-operator.aspx](http://cprogramminglanguage.net/c-ternary-operator.aspx)

My first code example uses it.

---

### Post by smartbei on 2008-04-06
Just a balancing point - I like my functions returning as soon as possible. I check for an errr after every call and return if there was an error, with the appropriate error code. I haven't found it harder to debug this kind of code, YMMV. I believe this is mostly a matter of style.

BTW - I do think that using return instead of exit is nicer - more generic.

---

### Post by LaRoza on 2008-04-06
@OP You have entererd the religion of programmers. Except faith that could shake mountains and crash Debian.

---

### Post by nvteighen on 2008-04-06
> **LaRoza said:**
> @OP You have entererd the religion of programmers. Except faith that could shake mountains and crash Debian.
:) Well, I have some prior experience...

I'm rewritting the code; mainly modularizing it. It's really hard, but now I understand how difficult is to maintain a code with an overloaded main()!

On returning and so, I'll see what style to follow only after having cleaned main()...

---

### Post by nvteighen on 2008-04-06
OK, here's a rewritten version of the code. I've tried to make main() as concise as I could, but I feel there's a lot much there to do.

I've followed smartbei's advice to use returns on error instead of using a variable value and just one return at main()'s end.

[PHP]
/*A D'Hondt/Hagenbach-Bischoff Method implementation in C
*
*    Copyright (c) 2008 Eugenio M. Vigo
*
*    This program is free software: you can redistribute it and/or modify
*    it under the terms of the GNU General Public License as published by
*    the Free Software Foundation, either version 3 of the License, or
*    (at your option) any later version.
*
*    This program is distributed in the hope that it will be useful,
*    but WITHOUT ANY WARRANTY; without even the implied warranty of
*    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*    GNU General Public License for more details.
*
*    You should have received a copy of the GNU General Public License
*    along with this program.  If not, see <http://www.gnu.org/licenses/>
*
*/

#include <stdio.h>
#include <stdlib.h>

int alloc_test(void *a, void *b, void *c)
{
	if((a == NULL)||(b == NULL)||(c == NULL))
	{
		perror("dhondt");
		return 3;
	}
	return 0;
}

void readv(int *vot, int *vtot, FILE *data, int n)
{
	int i;
	
	for(i = 0; i < n; i++)
	{
		fscanf(data, "%d", &vot[i]); //assigning 
		*vtot += vot[i]; //Calculating total amount of votes
	}
}

void calcs(int *vot, int *tot_real, int *seats, int vtot, int tot, int n)
{
	int i;
	float wz = vtot / (tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1

	for(i = 0; i < n; i++)
	{
		seats[i] = (int)(vot[i] / wz);
		*tot_real += seats[i];
	}
}

float hb2(int v, int d)
{
	float output;
	output = v / (d + 1); //Droop quota applied
	
	return output;
}


int exam_max(float *q, int n)
{
	int output, i;
	float o;
	
	//Primitive way to choose the largest value from a given list.
	o = 0;
	for(i = 0; i < n; i++)
	{	
		if(q[i] > o)
		{
			o = q[i];
			output = i;
		}
	}
	
	return output;
}

void hb(float *q, int *vot, int *seats, int *tot_real, int n)
{
	int a = 0;
	int i = 0;
	
	for(i = 0; i < n; i++)		
		q[i] = hb2(vot[i], seats[i]);
	a = exam_max(q, n);
	seats[a]++;
	tot_real++;
}

int main(int argc, char **argv)
{
	FILE *data;
	int c = 0, i = 0, n = -1, a = 0;
	int tot = 0, tot_real = 0, vtot = 0;
	int *seats, *vot;
	float *q;

	if(argc != 2)
	{
		//Exiting if no file specified or if too much arguments used.
		puts("Usage: dhondt FILENAME");
		return 1;
	}	

	if((data = fopen(argv[1], "r")) == NULL)
	{
		//Opening and testing file. If failed, exiting.
		perror("dhondt");	
		return 2;
	}
	
	/*Check in how many parties will the seats be apportioned by counting the amount of 		integers there are.*/
	while(fscanf(data, "%d", &c) != EOF)
		n++;
	rewind(data); //Rewinding file.
	
	/*Surely heap can be avoided, but I'm not aware how. So, I'm forced to dynamic allocation
	vot = array of votes by each party
	seats = array of number of seats
	q = quota for each party.*/
	vot = malloc(n * sizeof(int));
	seats = malloc(n * sizeof(int));
	q = malloc(n * sizeof(float));
	a = alloc_test(vot, seats, q); //Calling a function to test whether malloc succeeded or not.
	if(a == 3)
		return 3;

	//The first number in the file will be treated as the total amount of seats.
	fscanf(data, "%d", &tot);
	
	readv(vot, &vtot, data, n); //Reading the rest of the file.
	fclose(data); //Closing the file. We don't need it any longer.
	
	/*Now we'll calculate seats without caring for the decimal part.*/
	calcs(vot, &tot_real, seats, vtot, tot, n);
	
	/*But as D'Hondt uses down-rounding, tot_real will very probably be some seats smaller than the total amount of seats we wanted to apportion. Here we use the Hagenbach-Bischoff method, a so-called "static" apportionment method: we divide each party's votes by the seats it already has plus 1. One seat is given to the party having the largest quotient. This is repeated until no more seats are needed to apportion.*/
	if(tot_real < tot)
	{
		hb(q, vot, seats, &tot_real, n);
	}
	free(q); //Free malloc'd memory.

	for(i = 0; i < n; i++)
		printf("%d\n", seats[i]);
	
	//Free malloc'd memory.	
	free(vot);
	free(seats);
	return 0;
}
[/PHP]

---

### Post by dwhitney67 on 2008-04-06
Please see my code changes and comments below... and please be aware that I did not attempt to compile, but if I had, I would have used the 1999 standards.

Variables should be declared closest (or within the block) where they are needed.  Try to avoid polluting an entire block with a variable that is only needed in a small space (e.g. a for-loop).

Use malloc (and calloc) only when necessary.  In your program, memory allocation off of the heap  is not necessary.

Also, define useful names for your variables in lieu of single-character names, unless it is intuitively obvious what the variable represents.


> **nvteighen said:**
> OK, here's a rewritten version of the code. I've tried to make main() as concise as I could, but I feel there's a lot much there to do.

I've followed smartbei's advice to use returns on error instead of using a variable value and just one return at main()'s end.

[PHP]
/*A D'Hondt/Hagenbach-Bischoff Method implementation in C
*
*    Copyright (c) 2008 Eugenio M. Vigo
*
*    This program is free software: you can redistribute it and/or modify
*    it under the terms of the GNU General Public License as published by
*    the Free Software Foundation, either version 3 of the License, or
*    (at your option) any later version.
*
*    This program is distributed in the hope that it will be useful,
*    but WITHOUT ANY WARRANTY; without even the implied warranty of
*    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
*    GNU General Public License for more details.
*
*    You should have received a copy of the GNU General Public License
*    along with this program.  If not, see <http://www.gnu.org/licenses/>
*
*/

#include <stdio.h>
#include <stdlib.h>

/*
int alloc_test(void *a, void *b, void *c)
{
	if((a == NULL)||(b == NULL)||(c == NULL))
	{
		perror("dhondt");
		return 3;
	}
	return 0;
}
*/

void readv(int *vot, int *vtot, FILE *data, int n)
{
	/* int i; */
	
	for(int i = 0; i < n; i++)    // declare variable at closed point to where needed
	{
		fscanf(data, "%d", &vot[i]); //assigning 
		*vtot += vot[i]; //Calculating total amount of votes
	}
}

void calcs(int *vot, int *tot_real, int *seats, int vtot, int tot, int n)
{
	/* int i; */
	float wz = vtot / (tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1

	for(int i = 0; i < n; i++)   // declare variable at closed point to where needed
	{
		seats[i] = (int)(vot[i] / wz);
		*tot_real += seats[i];
	}
}

float hb2(int v, int d)
{
	/* float output;
	output = v / (d + 1); //Droop quota applied
	
	return output; */

        return v/(d +1);    // no need to declare variables if they are not needed
}


int exam_max(float *q, int n)
{
	/* int output, i;
	float o; */

        // always initialize variables that will be used to return values!
        int indexLargestValue = 0;
	
	//Primitive way to choose the largest value from a given list.
	/* o = 0; */
	for(int i = 1; i < n; i++)   // start from index 1, not zero.  Assume index 0 is the largest until otherwise proven.
	{	
		if(q[i] > q[indexLargestValue])
		{
			indexLargestValue = i;
		}
	}
	
	return indexLargestValue;
}

void hb(float *q, int *vot, int *seats, int *tot_real, int n)
{
	/* int a = 0; */
	/* int i = 0; */
	
	for(int i = 0; i < n; i++)		
		q[i] = hb2(vot[i], seats[i]);
	const int a = exam_max(q, n);
	seats[a]++;
	tot_real++;
}

int main(int argc, char **argv)
{
	FILE *data;  // initialize this to NULL (or zero)
	int c = 0, i = 0, n = -1, a = 0;
	int tot = 0, tot_real = 0, vtot = 0;
	/* int *seats, *vot; */
	float *q;  // initialize this to NULL (or zero), or see below

	if(argc != 2)
	{
		//Exiting if no file specified or if too much arguments used.
		puts("Usage: dhondt FILENAME");
		return 1;
	}	

	if((data = fopen(argv[1], "r")) == NULL)
	{
		//Opening and testing file. If failed, exiting.
		perror("dhondt");	
		return 2;
	}
	
	/*Check in how many parties will the seats be apportioned by counting the amount of 		integers there are.*/
        int n = 0, c;
	while(fscanf(data, "%d", &c) != EOF)
		n++;
	rewind(data); //Rewinding file.
	
	/*Surely heap can be avoided, but I'm not aware how. So, I'm forced to dynamic allocation
	vot = array of votes by each party
	seats = array of number of seats
	q = quota for each party.*/

/*
	vot = malloc(n * sizeof(int));
	seats = malloc(n * sizeof(int));
	q = malloc(n * sizeof(float));
	a = alloc_test(vot, seats, q); //Calling a function to test whether malloc succeeded or not.
	if(a == 3)
		return 3;
*/
        // alternatively...
        int vot[ n ];
        int seats[ n ];
        float q[ n ];


	//The first number in the file will be treated as the total amount of seats.
	fscanf(data, "%d", &tot);
	
	readv(vot, &vtot, data, n); //Reading the rest of the file.
	fclose(data); //Closing the file. We don't need it any longer.
	
	/*Now we'll calculate seats without caring for the decimal part.*/
	calcs(vot, &tot_real, seats, vtot, tot, n);
	
	/*But as D'Hondt uses down-rounding, tot_real will very probably be some seats smaller than the total amount of seats we wanted to apportion. Here we use the Hagenbach-Bischoff method, a so-called "static" apportionment method: we divide each party's votes by the seats it already has plus 1. One seat is given to the party having the largest quotient. This is repeated until no more seats are needed to apportion.*/
	if(tot_real < tot)
	{
		hb(q, vot, seats, &tot_real, n);
	}
	// free(q); //Free malloc'd memory.

	for(int i = 0; i < n; i++)
		printf("%d\n", seats[i]);
	
	//Free malloc'd memory.	
	// free(vot);
	// free(seats);
	return 0;
}
[/PHP]

---

### Post by nvteighen on 2008-04-06
> **dwhitney67 said:**
> Please see my code changes and comments below... and please be aware that I did not attempt to compile, but if I had, I would have used the 1999 standards.

Variables should be declared closest (or within the block) where they are needed.  Try to avoid polluting an entire block with a variable that is only needed in a small space (e.g. a for-loop).

Use malloc (and calloc) only when necessary.  In your program, memory allocation off of the heap  is not necessary.

Also, define useful names for your variables in lieu of single-character names, unless it is intuitively obvious what the variable represents.

Your version compiles, but leads to a core dump. If I only restore heap allocation, the program works correctly again... so, now the question is when is heap necessary?

Something I don't understand is why in hb() you declare a as a constant.

Anyway, thanks for your advices! The code looks much better than before.

---

### Post by dwhitney67 on 2008-04-06
> **nvteighen said:**
> Your version compiles, but leads to a core dump. If I only restore heap allocation, the program works correctly again... so, now the question is when is heap necessary?

Something I don't understand is why in hb() you declare a as a constant.

Anyway, thanks for your advices! The code looks much better than before.

I will look into the core dump thing later.  Right now I am pressed for time.

Concerning declaring 'a' as a constant, that is merely the "PC" (politically correct) way to declare a value that will not change.  In the case of your application, it seemed appropriate to do it there.

Anyhow, I will try to get back to your code (w/ my changes) this evening.

Cheers.

---

### Post by dwhitney67 on 2008-04-06
> **nvteighen said:**
> Your version compiles, but leads to a core dump. If I only restore heap allocation, the program works correctly again... so, now the question is when is heap necessary?

Something I don't understand is why in hb() you declare a as a constant.

Anyway, thanks for your advices! The code looks much better than before.
I would like to troubleshoot the core dump problem.  Please attach (using the paper-clip symbol above) your data file that contains the seats and votes for each party.  You may need to rename your data file to have a .txt extension so that the forum is "happy".

---

### Post by dwhitney67 on 2008-04-07
I haven't heard back concerning the format of the data file, so I assumed based on the original code posted that it contained a single line that specified the number of seats available for the election, followed by the number of votes cast for each party.

I was able to get the original code working (see orig.tar), however I was not satisfied with the need to read the data from the file two times, nor was I satisfied that the data for the quotients was not saved during runtime (and hence could not be printed for analysis).

Thus I rewrote the application, and to save myself the hassle of reading the file a second time, I thought it would be easier if the data file contained a field that specified the number of parties.  You can see my work (and the data file) in new.tar.

Enjoy!

P.S.  What is missing, and would be nice to see, is a marker to indicate which party won the seat.  This information would supplement the seat count that the party won.

P.S.S.  Here's the source code contained in new.tar:
[PHP]#include <stdio.h>
#include <stdlib.h>

#define TRUE  1
#define FALSE 0


// Reads the data from the file, which includes the number of seats, the
// number of parties, and the votes cast for each party.
//
// Returns TRUE if all of the data is read; FALSE otherwise.
//
// Note that system memory is allocated for votesCast, and thus must be
// freed by the caller.
//
int ReadDataFile( FILE *fp, int *numSeats, int *numParties, int **votesCast )
{
  iif ( fscanf( fp, "%d %d", numSeats, numParties ) != 2 )
  {
    return FALSE;
  }

  *votesCast = malloc( *numParties * sizeof(int) );

  if ( votesCast == 0 )
  {
    return FALSE;
  }

  for ( int i = 0; i < *numParties; ++i )
  {
    if ( fscanf( fp, "%d", &(*votesCast)[i] ) != 1 )
    {
      return FALSE;
    }
  }

  return TRUE;
}


// Calculate the number of seats that will be allocated to each
// party.  While at it, keep track of the individual party quotients
// that are derived for each seat.
//
void calculateSeats( const int numSeats,
                     const int numParties,
                     const int *votesCast,
                     int *partySeats,
                     int *partyQuotients )
{
  // initially all parties have zero seats each
  for ( int p = 0; p < numParties; ++p )
  {
    partySeats[p] = 0;
  }

  // determine how the seats will be allocated to the parties
  for ( int s = 0; s < numSeats; ++s )
  {
    int highVote = 0;

    for ( int p = 0; p < numParties; ++p )
    {
      const int pqIndex = s * numParties + p;

      partyQuotients[ pqIndex ] = votesCast[p] / (partySeats[p] + 1 );

      highVote = partyQuotients[ pqIndex ] > highVote ? partyQuotients[ pqIndex ] : highVote;
    }

    for ( int p = 0; p < numParties; ++p )
    {
      const int pqIndex = s * numParties + p;

      if ( highVote == partyQuotients[ pqIndex ] )
      {
        partySeats[p]++;
        break;
      }
    }
  }
}


// The function name says it all... display the election results.
//
void displayResults( const int numSeats,
                     const int numParties,
                     const int *votesCast,
                     const int *partySeats,
                     const int *partyQuotients )
{
  printf( "\t\t" );

  for ( int p = 0; p < numParties; ++p )
  {
    printf( "Party %c\t\t", 'A' + p );
  }

  printf("\nVotes\t\t");
  for ( int p = 0; p < numParties; ++p )
  {
    printf( "%d\t\t", votesCast[p] );
  }

  for ( int s = 0; s < numSeats; ++s )
  {
    printf("\nSeat %d", s );

    for ( int p = 0; p < numParties; ++p )
    {
      printf( "\t\t%d", partyQuotients[ s * numParties + p ] );
    }
  }

  printf( "\nTotal" );
  for ( int p = 0; p < numParties; ++p )
  {
    printf( "\t\t%d", partySeats[p] );
  }

  printf("\n");
}


// Main program.  A filename containing election results is expected.
int main( int argc, char **argv )
{
  if ( argc != 2 )
  {
    printf( "Usage: %s dhondt-data\n", argv[0] );
    return 1;
  }

  FILE *data = 0;

  if ( (data = fopen( argv[1], "r" )) == 0 )
  {
    printf( "Error:  Unable to open file %s\n", argv[1] );
    return 2;
  }

  int numSeats   = 0;
  int numParties = 0;
  int *votesCast = 0;

  if ( ReadDataFile( data, &numSeats, &numParties, &votesCast ) == TRUE )
  {
    int partySeats[ numParties ];
    int partyQuotients[ numSeats ][ numParties ];

    calculateSeats( numSeats, numParties, votesCast, partySeats, &partyQuotients[0][0] );

    displayResults( numSeats, numParties, votesCast, partySeats, &partyQuotients[0][0] );

    free( votesCast );
  }
  else
  {
    printf( "Error:  Internal problem prevented the reading of the data file %s\n", argv[1] );
    return 3;
  }

  return 0;
}[/PHP]

---

### Post by nvteighen on 2008-04-07
> **dwhitney67 said:**
> I haven't heard back concerning the format of the data file, so I assumed based on the original code posted that it contained a single line that specified the number of seats available for the election, followed by the number of votes cast for each party.

I was able to get the original code working (see orig.tar), however I was not satisfied with the need to read the data from the file two times, nor was I satisfied that the data for the quotients was not saved during runtime (and hence could not be printed for analysis).

Thus I rewrote the application, and to save myself the hassle of reading the file a second time, I thought it would be easier if the data file contained a field that specified the number of parties.  You can see my work (and the data file) in new.tar.

Enjoy!

P.S.  What is missing, and would be nice to see, is a marker to indicate which party won the seat.  This information would supplement the seat count that the party won.

P.S.S.  Here's the source code contained in new.tar:


Hi, sorry: I couldn't read your reply before.

Well, I tried to implement the party's marker, but for some reason it got me into an infinite loop. That was right before I cleaned main() up, so possibly I was giving that instruction where I shouldn't have.

Well, I see you have done a lot in it and I'm going to spend some time to track what you've done! Hey, thank you for this "lecture" ;)

I'm going to see your code in more detail today later. I'm a bit busy today....

---

### Post by nvteighen on 2008-04-07
Ah, the file! It's a slightly modified version from Wikipedia's example (598 seats instead of 7 seats... 598 is the size of German Bundestag)

---

### Post by nvteighen on 2008-04-07
OK. I've reviewed my code a bit more and used some of your ideas.

#Tried to declare variables where nearest as possible to first use. Sorry for the variables' names...
#Changed program's output in order to show party's votes and seats. Not quota because it's irrelevant for a D'Hondt-driven election. (It's different for each party... actually D'Hondt is quasi-proportional allocation, but it's the most popular system used).
#Don't used C99 Standard. Yes, I see the advantages of declaring i inside a for..., but just it doesn't fit with my style.
#Have read your second code. Well, that's really more ordered than my code. I'll try now to cut my main module down.

[PHP]
#include <stdio.h>
#include <stdlib.h>

int alloc_test(void *a, void *b, void *c)
{
	if((a == NULL)||(b == NULL)||(c == NULL))
	{
		perror("dhondt");
		return 3;
	}
	return 0;
}

void readv(int *vot, int *vtot, FILE *data, int n)
{	
	int i;
	for(i = 0; i < n; i++)
	{
		fscanf(data, "%d", &vot[i]); //assigning 
		*vtot += vot[i]; //Calculating total amount of votes
	}
}

void calcs(int *vot, int *tot_real, int *seats, int vtot, int tot, int n)
{
	float wz = (float)vtot / (float)(tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1
	
	int i;
	for(i = 0; i < n; i++)
	{
		seats[i] = (int)(vot[i] / wz);
		*tot_real += seats[i];
	}
}

float hb2(int v, int d)
{
	return (v / (d + 1));
}


int exam_max(float *q, int n)
{
	int output = 0;
	
	int i;
	//Primitive way to choose the largest value from a given list.
	for(i = 1; i < n; i++)
	{	
		if(q[i] > q[output])
		{
			output = i;
		}
	}
	
	return output;
}

void hb(float *q, int *vot, int *seats, int *tot_real, int n)
{
	int i;
	
	for(i = 0; i < n; i++)		
		q[i] = hb2(vot[i], seats[i]);

	int a = exam_max(q, n);
	
	seats[a]++;
	tot_real++;
}

int main(int argc, char **argv)
{
	if(argc != 2)
	{
		//Exiting if no file specified or if too much arguments used.
		puts("Usage: dhondt FILENAME");
		return 1;
	}	

	FILE *data = NULL;
	if((data = fopen(argv[1], "r")) == NULL)
	{
		//Opening and testing file. If failed, exiting.
		perror("dhondt");	
		return 2;
	}
	
	//Check in how many parties will the seats be apportioned by counting the amount of 		integers there are.
	int c = 0;
	int n = -1;
	while(fscanf(data, "%d", &c) != EOF)
		++n;
	rewind(data); //Rewinding file.
	
	int tot = 0;	
	//The first number in the file will be treated as the total amount of seats.
	fscanf(data, "%d", &tot);
	printf("Total of seats: %d\n\n", tot);
	
	//Surely heap can be avoided, but I'm not aware how. So, I'm forced to dynamic allocation 		vot = array of votes by each party, seats = array of number of seats, q = quota for each 		party.

	int *vot = malloc(n * sizeof(int));
	int *seats = malloc(n * sizeof(int));
	float *q = malloc(n * sizeof(float));
	int a = alloc_test(vot, seats, q); //Calling a function to test whether malloc succeeded or not.
	if(a == 3)
		return 3;
	
	int vtot = 0;
	readv(vot, &vtot, data, n); //Reading the rest of the file.
	fclose(data); //Closing the file. We don't need it any longer.
	
	//Now we'll calculate seats without caring for the decimal part.
	int tot_real = 0;
	calcs(vot, &tot_real, seats, vtot, tot, n);
	
	/*
	But as D'Hondt uses down-rounding, tot_real will very probably be some seats smaller 		than the total amount of seats we wanted to apportion. Here we use the Hagenbach-Bischoff 		method, a so-called "static" apportionment method: we divide each party's votes by the 		seats it already has plus 1. One seat is given to the party having the largest quotient. 		This is repeated until no more seats are needed to apportion.
	*/

	if(tot_real < tot)
	{
		hb(q, vot, seats, &tot_real, n);
	}
	free(q); //Free malloc'd memory.

	puts("Party\t Votes\t Seats\n");
	int i;
	for(i = 0; i < n; i++)
	{
		printf("%c:\t %d\t %d\n", 'A' + i, vot[i], seats[i]);
	}
	
	//Free malloc'd memory.	
	free(vot);
	free(seats);
	return 0;
}
[/PHP]

---

### Post by dwhitney67 on 2008-04-07
I don't know much about D'Hondt... only about what I read on Wikipedia (or something similar).  Thus the output I generated (including the quotients) reflects what I saw listed on that page.  I sorted of reversed engineered the problem.

One thing I did not understand clearly about your original code was the purpose for this statement:
[PHP]    float wz = (float)vtot / (float)(tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1 [/PHP]

I did not come across this in the Wiki-page concerning D'Hondt.  Is this an extension of the algorithm?

Concerning programming style, choose whichever you please, however bear in mind that if you ever do programming for an organization that has programming standards in place, you may have to chuck your ways and adopt theirs.

The notion of declaring and initializing variables closest to where they are needed is not a new concept.  It has been adopted by many organizations that emphasize Information Assurance (IA) procedures when developing software to mitigate errors (bugs) in code.  The C99 standards are now 9 years old.  There is no value in using C standards that are much older than that!

---

### Post by ruy_lopez on 2008-04-07
It's better to wrap large comments in a block, than have them scroll off the right side of the screen.

e.g.
```

/* a very large comment which goes on and on and on and on and runs off the right side of the screen */

```

```

/* another large comment. But this one is contained in
 * a block. It's easier to read, and won't slow down the
 * text-editor. */

```

---

### Post by nvteighen on 2008-04-07
> **dwhitney67 said:**
> I don't know much about D'Hondt... only about what I read on Wikipedia (or something similar).  Thus the output I generated (including the quotients) reflects what I saw listed on that page.  I sorted of reversed engineered the problem.
In other related algorithms it could be relevant. Maybe at exact proportion allocation methods, so you can show the quota is the almost the same for each party?

> One thing I did not understand clearly about your original code was the purpose for this statement:
[PHP]    float wz = (float)vtot / (float)(tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1 [/PHP]

I did not come across this in the Wiki-page concerning D'Hondt.  Is this an extension of the algorithm?

Well, seats allocation algorithms' essential difference is which "quota" is used. The quota is what really defines how the rounding will be made (14.6 are 14 or 15 seats?? You didn't get 15, but you have more than 14 too!). What I'm following here is Hagenbach-Bischoff's approach to "down rounding". "Real" D'Hondt actually uses a table like Wikipedia shows you... And Jefferson uses recursive approximation (which is the oldest and most difficult way to do this). But all this three apportionment methods are commonly grouped and addressed simply as "D'Hondt", just like the arithmetic rounding methods are all called "Saint Laguë".


> Concerning programming style, choose whichever you please, however bear in mind that if you ever do programming for an organization that has programming standards in place, you may have to chuck your ways and adopt theirs.

The notion of declaring and initializing variables closest to where they are needed is not a new concept.  It has been adopted by many organizations that emphasize Information Assurance (IA) procedures when developing software to mitigate errors (bugs) in code.  The C99 standards are now 9 years old.  There is no value in using C standards that are much older than that!

The reason why I declared variables at beginning was because of a misunderstanding on how C is compiled (in Javascript, I always declare variables and initialize as you say). Of course, if I ever get a programming job (not very possible, though: I'm a Linguistics student... I program because there are languages involved!) I'd have to stick to whatever standard I'm told to follow (just like when someone tells me to do an essay in a format I don't like).

Thanks for your help! I'm going to post a new version of the code in a separate post.

---

### Post by nvteighen on 2008-04-07
Here it is!

[PHP]
/*  A D'Hondt/Hagenbach-Bischoff implementation in C
 *  Copyright (C) 2008  Eugenio M. Vigo
 *
 *  This program is free software: you can redistribute it and/or modify
 *  it under the terms of the GNU General Public License as published by
 *  the Free Software Foundation, either version 3 of the License, or
 *  (at your option) any later version.
 *
 *  This program is distributed in the hope that it will be useful,
 *  but WITHOUT ANY WARRANTY; without even the implied warranty of
 *  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *  GNU General Public License for more details.
 *
 *  You should have received a copy of the GNU General Public License
 *  along with this program.  If not, see <http://www.gnu.org/licenses/>.
 */

#include <stdio.h>
#include <stdlib.h>

void readv(int **vot, int *vtot, int **seats, int *tot, FILE *data, int *n)
{	
	int c = 0;
	while(fscanf(data, "%d", &c) != EOF)
		++(*n);
	rewind(data);
	
	*vot = malloc(*n * sizeof(int));
	*seats = malloc(*n * sizeof(int));

	if((vot == NULL)||(seats == NULL))
	{
		puts("dhondt: Internal error");
		exit(3);
	}
	
	fscanf(data, "%d", tot);
	
	int i;
	for(i = 0; i < *n; i++)
	{
		fscanf(data, "%d", &(*vot)[i]);
		*vtot += (*vot)[i];
	}

	fclose(data);
}

void calcs(int *vot, int *tot_real, int *seats, int vtot, int tot, int n)
{
	float wz = vtot / (tot + 1); //D'Hondt uses the Droop quota Q = V / S + 1
	
	int i;
	for(i = 0; i < n; i++)
	{
		seats[i] = (int)(vot[i] / wz);
		*tot_real += seats[i];
	}
}

float hb2(int v, int d)
{
	return (v / (d + 1));
}


int exam_max(float *q, int n)
{
	int output = 0;
	
	int i;
	for(i = 1; i < n; i++)
	{	
		if(q[i] > q[output])
		{
			output = i;
		}
	}
	
	return output;
}

void hb(int *vot, int *seats, int *tot_real, int n)
{
	int i;
	
	float *q = malloc(n * sizeof(float));
	if(q == NULL)
	{
		puts("dhondt: Internal error");
		exit(3);
	}
	for(i = 0; i < n; i++)		
		q[i] = hb2(vot[i], seats[i]);

	int a = exam_max(q, n);
	
	seats[a]++;
	tot_real++;

	free(q);
}

int main(int argc, char **argv)
{
	if(argc != 2)
	{
		puts("Usage: dhondt FILENAME");
		exit(1);
	}	

	FILE *data = NULL;
	if((data = fopen(argv[1], "r")) == NULL)
	{
		perror("dhondt");	
		exit(2);
	}

	int n = -1;
	int tot = 0;
	int vtot = 0;
	int *vot = NULL, *seats = NULL;

	readv(&vot, &vtot, &seats, &tot, data, &n);
	
	int tot_real = 0;
	calcs(vot, &tot_real, seats, vtot, tot, n);

	if(tot_real < tot)
		hb(vot, seats, &tot_real, n);

	puts("Party\t Votes\t Seats\n");
	int i;
	for(i = 0; i < n; i++)
	{
		printf("%c:\t %d\t %d\n", 'A' + i, vot[i], seats[i]);
	}
	
	free(vot);
	free(seats);
	return 0;
}[/PHP]

---

