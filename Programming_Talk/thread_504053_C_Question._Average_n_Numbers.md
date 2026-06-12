---
title: "C Question. Average n Numbers"
date: 2007-07-18
forum: Programming Talk
---

### Post by TreeFinger on 2007-07-18
I am still reading my book on C programming language. I am on an exercise which asks to write a program to find the average of n numbers.

I can easily write the program but I am trying to figure out a way to exit the while loop. I believe the word is sentinel value? It can't be a number, I tried double zeros but the loop also exits when one zero is typed.

I can't use a letter because the input is %f ( float ).

While I was typing this I am thinking that a switch statement would probably be the way to go. Is that a clue that most of you experienced programmers would have gave me?

Thanks for the time reading this, I'll attach my code.

```

/* Programming exercises. Chapter 8-3
*  Created by Samuel Chodur Jr.
*  Program: Finds Average of n Numbers
*/

#include <stdio.h>
char input[1000];
float temp; /* temporary storage for numbers entered */
int num_count; /* number to divide total by */
float total; /* Total of numbers entered */
float average; /* 'total' divided by 'num_count' */

int main() {
	/* Tell user what program does */
	printf("I will find the average of however many numbers you enter.\n");
	printf("Enter number now (00 to quit): ");
	
	/* Accept first input from user */
	fgets(input, sizeof(input), stdin);
	sscanf(input, "%f", &temp);

	/* Initalize Variables */
	num_count = 0;
	total = 0.0;
	average = 0.0;

	while ( temp != 00.0 ) {
		++num_count; /* increases with each number entered */
		total += temp; /* adds all numbers entered to total */
		temp = 0; /* clears temp variable */
		
		printf("Enter next number now (00 to quit): ");
		fgets(input, sizeof(input), stdin);
		sscanf(input, "%f", &temp);
	}
	average = ( total / num_count );
	printf("You entered %d numbers. The average of those numbers is %f.\n", num_count, average);

return 0;
}

```

---

### Post by rodo-&gt;dave on 2007-07-18
One way you could do it is to set the while loop to run then test the input with an if statement and do a break

```

#include <stdio.h>

int main(int argc, char **argv)
{
    float x = 0.0;

    while (1)
    {
        printf("Enter a number: ");
        scanf("%f", &x);

        if (x == 0)
            break;

        printf("You typed: %f\n", x);

    }

    return(0);
}

```

---

### Post by nitro_n2o on 2007-07-18
unfortunately left zeros don't count so 0000.0 is the same as 00.00000 and the same as 0.0 and the same as 0f.. if you want to quit on 00 you need to parse it as a string check it then decide what to do 
you can convert from a string to float using atof 

Have fun :)

---

### Post by Mr. C. on 2007-07-18
```
    while (fgets(buf, 100, stdin) != NULL) {
        process input ...
    };

```

MrC

---

### Post by TreeFinger on 2007-07-18
Well thanks for the replies, I think I figured it out myself with a switch statement. Seems to work perfectly for me right now, if you wanna test, go ahead :o

```

/* Programming exercises. Chapter 8-3
*  Created by Samuel Chodur Jr.
*  Program: Finds Average of n Numbers
*/

#include <stdio.h>

char input[1000];
char choice; /* User selection */
float temp; /* temporary storage for numbers entered */
int num_count; /* number to divide total by */
float total; /* Total of numbers entered */
float average; /* 'total' divided by 'num_count' */

int main() {
	/* Tell user what program does */
	printf("I will find the average of however many numbers you enter.\n");
	printf("To enter a number type n. To quit and get average type q.\n");

	/* Initalize Variables */
	num_count = 0;
	total = 0.0;
	average = 0.0;

while (1) {
	/* User chooses to input number or quit and get average */
	printf("Enter choice now(n or q): ");
	fgets(input, sizeof(input), stdin);
	sscanf(input, "%c", &choice);

	switch (choice) {
		case 'N':
		case 'n': /* User chooses to enter another number */
			printf("Enter number now: ");
			fgets(input, sizeof(input), stdin);
			sscanf(input, "%f", &temp);
			++num_count; /* increases with each number entered */
			total += temp; /* adds all numbers entered to total */
			temp = 0; /* clears temp variable */
			continue;
		case 'Q':
		case 'q': /* User chooses to quit and get average */
			break;
		default: /* User enteres invalid option */
			printf("Invalid choice entered.\n");
			continue;
	}
	break; /* Break from while loop */
}
	average = ( total / num_count );
	printf("You entered %d numbers. The average of those numbers is %f.\n", num_count, average);

return 0;
}

```

---

### Post by yabbadabbadont on 2007-07-18
Your solution looks fine.  As a matter of personal taste, I prefer to use a construct more like this:
```

Done = FALSE;  /* or 0 if you prefer */

while (!Done)
{
    ....
    switch (choice)
    {
        ....
       case 'Q':
       case 'q':
           Done = TRUE;
           break;
        ....
    }
}
```

---

### Post by TreeFinger on 2007-07-18
> **yabbadabbadont said:**
> Your solution looks fine.  As a matter of personal taste, I prefer to use a construct more like this:
```

Done = FALSE;  /* or 0 if you prefer */

while (!Done)
{
    ....
    switch (choice)
    {
        ....
       case 'Q':
       case 'q':
           Done = TRUE;
           break;
        ....
    }
}
```


Does that involve boolean? My book hasn't gotten to that point yet.

---

### Post by Mr. C. on 2007-07-18
> **TreeFinger said:**
> Does that involve boolean? My book hasn't gotten to that point yet.

There is no boolean type in C.  They are emulated as ints or chars, with 0 and non-0 or 1 values, often defined with the macros as:

#define FALSE 0
#define TRUE  1

or similar.

MrC

---

### Post by yabbadabbadont on 2007-07-18
> **Mr. C. said:**
> There is no boolean type in C.  They are emulated as ints or chars, with 0 and non-0 or 1 values, often defined with the macros as:

#define FALSE 0
#define TRUE  1

or similar.

MrC
What he said.  :D

---

